---
title: ZEISS Vision Care - Order Fulfillment
date: 2026-03-17

org_name: ZEISS
org_team: Business Enablement & IT
org_url: https://zeiss.com
org_logo_filename: images/zeiss-logo-rgb.svg
contact: Fabian Steinbach
email: fabian.steinbach@zeiss.com
org_description: |
  ZEISS Vision Care produces spectacle lenses, instruments for refraction, and
  glasses adjustment equipment. A global production network supports consistent
  and reliable order fulfillment across regions. Spectacle lenses are often
  individually produced for each consumer, which adds complexity to planning,
  manufacturing, and logistics.
org_size: "10,000+"
user_size: "Order processing system (not user-facing)"
industries:
  - optics
  - optical-manufacturing
tags:
  - public-cloud
  - mass-manufacturing
  - industry
  - microservices
  - platform engineering

categories:
  host-platform: [ "aks", "containerd" ]
  orchestration: [ "kubernetes" ]
  observability: [ "otel", "otel-collector" ]
  messaging: [ "azure-service-bus", "dapr-pubsub" ]
  storage: [ "mssql", "cosmos-db", "azure-blob-storage", "redis"]
  other-projects: [ "dapr", "keda", "helm" ]

reference_architectures:
  - Microservices
  - Platform Engineering
---

## Relevant CNCF projects

{{< cardpane >}}
  {{< card header="Kubernetes" >}}
  [![kubernetes logo](https://raw.githubusercontent.com/cncf/artwork/main/projects/kubernetes/icon/color/kubernetes-icon-color.svg)](https://www.cncf.io/projects/kubernetes/)
  - **Using since:** 2020
  - **Current version:** 1.32.3

  Hosts > 200 microservices supporting order fulfillment processes on managed Kubernetes. Provides the core compute platform for containerized services.
  {{< /card >}}

  {{< card header="Dapr" >}}
  [![dapr logo](https://raw.githubusercontent.com/cncf/artwork/main/projects/dapr/stacked/color/dapr-stacked-color.svg)](https://www.cncf.io/projects/dapr/)
  - **Using since:** 2020
  - **Current version:** 1.17.0

  Provides common building blocks like service invocation, pub/sub, and state management across microservices; vendor-neutral abstractions enable portability across cloud providers.
  {{< /card >}}

  {{< card header="KEDA" >}}
  [![keda logo](https://raw.githubusercontent.com/cncf/artwork/main/projects/keda/icon/color/keda-icon-color.svg)](https://www.cncf.io/projects/keda/)
  - **Using since:** 2021/2022
  - **Current version:** 2.19.0

  Event-driven scaling. KEDA acts as an event-driven scaler; examples of triggers include message-broker queue depth and resource utilization.
  {{< /card >}}

  {{< card header="OpenTelemetry" >}}
  [![opentelemetry logo](https://raw.githubusercontent.com/cncf/artwork/main/projects/opentelemetry/icon/color/opentelemetry-icon-color.svg)](https://www.cncf.io/projects/opentelemetry/)
  - **Using since:** 2020
  - **Current version:** Collector Contrib 0.145.0

  Provides consistent instrumentation and exports telemetry to multiple targets.
  {{< /card >}}

  {{< card header="Helm" >}}
  [![helm logo](https://raw.githubusercontent.com/cncf/artwork/main/projects/helm/icon/color/helm-icon-color.svg)](https://www.cncf.io/projects/helm/)
  - **Using since:** 2020

  Package management and templating for Kubernetes deployments.
  {{< /card >}}
{{< /cardpane >}}

## Organization
ZEISS Vision Care produces spectacle lenses, instruments for refraction, and glasses adjustment equipment. Often, lenses are manufactured to an individual consumer's prescription, effectively a batch size of one, which makes order fulfillment a multi-step coordination process.

Our Business Enablement & IT team develops, designs, and operates the order fulfillment platform that underpins this process.

## Synopsis
We are reworking the order fulfillment process using a greenfield approach to modernize core systems. Our goal is a reliable, scalable platform that can evolve with business needs while remaining cost-efficient. The platform supports several key capabilities:
- Order routing: decide where the order should be produced.
- Order document generation: generate the necessary manufacturing and shipping documents for the order.
- Logistics routing: decide how to ship the order to the customer.
- Additional auxiliary domains as required.

## Architecture overview & Goals

### Goals

The architecture is designed for future-proofing and scale. By leveraging event-driven scaling with KEDA and decoupled microservices via Dapr, the system is built to seamlessly absorb high-volume, global order loads as new processes are continuously migrated to the new platform.

**Key Requirements:**
- Modern cloud-based infrastructure
- High reliability and scalability
- Maintainable and extensible
- Cost-effective operations

### Architecture Overview
![Architecture](./images/solutionArchitecture.svg)

#### Data & Storage Strategy
The platform uses Azure-managed data services as backing stores:
- **MSSQL**: Transactional order data and relational schemas
- **Cosmos DB**: Scaled state management and cross-region replication
- **Azure Blob Storage**: Order documents and manufacturing files
- **Redis**: Caching operations to improve latency and throughput

Dapr's state abstraction layer is used for Cosmos DB, Azure Blob Storage, and Redis, decoupling microservices from those storage backends and enabling migrations without application-level changes. For Azure Blob Storage, we also use Dapr's blob binding to interact with data, in addition to the state abstraction layer.

#### Messaging & Asynchronous Communication
Azure Service Bus serves as the central message broker for asynchronous processes. Services publish and subscribe to topics via Dapr's pub/sub building block, enabling loose coupling between applications. This event-driven approach provides resilience and allows each service to scale independently based on demand.

#### Network & Service Discovery
Services use Dapr's service invocation building block instead of hardcoded endpoints, enabling resilience and the ability to replace or upgrade service implementations without changing callers. External traffic is routed to services via Ingress NGINX.

#### CI/CD & Deployment
Azure DevOps Pipelines automate building, testing, and deploying applications. We use a single, centralized Helm chart and store deployment configuration in Git as the single source of truth; the pipeline generates environment- and service-specific `values.yaml` files and deploys each service as its own Helm release to Kubernetes.

## Can you expand on why you are using those projects/services?
We rely heavily on CNCF projects and open-source tooling to form the backbone of our platform:

- **Kubernetes (AKS)** *(Using since 2020)*: Hosts > 200 microservices supporting order fulfillment workflows. It provides the core compute platform for containerized services, offering a flexible model that supports multiple frameworks, programming languages, and dynamic scaling.
- **Dapr** *(Using since 2020)*: Provides common building blocks like service invocation, pub/sub, and state management across microservices. Dapr enables vendor-neutral capabilities, addressing service discovery and maintaining portability.
- **KEDA** *(Using since 2021/2022)*: Event-driven scaling based on Azure Service Bus queue depth and CPU/memory utilization. This allows the system to scale aggressively to match real-time demand while running economically during quieter periods.
- **Helm**: Package management and templating. Charts are stored in Git, enabling reproducible deployments across environments since the project's inception.
- **Ingress NGINX** *(currently in use, pending replacement – see Future Outlook)*: External traffic routing and load balancing.
- **OpenTelemetry Collector** *(Using since 2020)*: Provides consistent instrumentation and exports telemetry to multiple targets. It enables distributed tracing and metrics collection across microservices, ensuring observability and performance monitoring.

## What has worked well?
Kubernetes, Helm, and KEDA have proven reliable and are widely used.

**Scaling to Zero and Back:**
We initially attempted to scale services to 0 replicas with KEDA to minimize costs, but this introduced operational challenges: delayed data flows during testing when pods needed to start up, and frequent scale churn during traffic pauses between messages. We learned that setting a minimum replica count for baseline load while scaling out for peaks was much more cost-effective and reliable for our specific workload patterns.

**The Advantage of Abstraction:**
A major architectural risk early on was building the entire system on Dapr (starting at pre-1.0 release 0.7.0). Early adoption carried organizational risk and we initially faced instability with actors under heavy load. Over time, those issues were fully resolved. The decision proved highly beneficial: Dapr’s maturity and vendor-neutral approach validated the initial decision, giving the platform extreme portability, flexibility, and saving custom boilerplate. 

**Platform Evolution:**
Dapr is consistently evolving, allowing us to streamline our platform by replacing specific SDKs with built-in functionalities over time. For instance, we are transitioning from Azure App Configuration to Dapr's Configuration Building Block. In hindsight, we would have standardized on CNCF native components sooner (e.g., migrating earlier to OpenTelemetry Collector and a CNCF ingress solution) to avoid replacing vendor-specific SDKs mid-project.

**Data Ownership and Boundaries:**
A critical lesson was the strict enforcement of data ownership. In a microservices architecture with over 200 services, we learned that clearly defining which service owns which data is non-negotiable. We found that any direct data access between services, bypassing their dedicated APIs, inevitably leads to tight coupling and maintenance challenges. Adhering to Domain-Driven Design (DDD) principles, where each service exposes its data only through a well-defined API, was essential for maintaining a scalable and evolvable system. This prevented a "distributed monolith" and ensured long-term architectural integrity.

## What sort of "glue" have you had to develop?

Since we had a greenfield start, we were not constrained by legacy endpoints or migration paths. However, managing over 200 microservices required strict boundaries and standardized communication patterns. We heavily utilized Domain-Driven Design (DDD) principles—specifically **Bounded Contexts** to ensure each microservice owns its data and domain logic.

To enforce these boundaries and standardize the "glue" between services, we developed:
- **Standardized Helm Templates**: A unified set of Helm charts that abstract away the complexity of Kubernetes manifests and Dapr sidecar configuration. Developers provide application-specific KEDA `ScaledObject` definitions and Dapr component definitions.
- **Common Libraries**: While Dapr abstracts away many infrastructure concerns, we built thin, language-specific wrappers around the Dapr SDKs to enforce internal logging and error-handling standards.

## Impact & Results
By adopting this cloud-native stack, we have built a highly scalable and future-ready order fulfillment system. A key driver of this success has been our extensive use of Dapr, which not only significantly reduced boilerplate code but also provided us with a high degree of vendor neutrality. This abstraction layer means we are not tightly coupled to specific cloud providers' SDKs, enabling an architecture that is portable, flexible, and robust enough for long-term growth.

## What's next for your architecture?
We are constantly investigating how to run our services as efficiently and economically as possible. A near-term priority is replacing our existing Ingress NGINX setup. Because the Kubernetes project has [officially announced the retirement of the ingress-nginx project](https://kubernetes.io/blog/2025/11/11/ingress-nginx-retirement/), we are actively evaluating alternatives—including NGINX Gateway Fabric, Envoy Gateway, and Traefik—while striving to preserve our routing behavior, TLS automation, and operational stability. Transitioning to the Gateway API is a key step in future-proofing our external traffic routing.

## Discussion
End user members may participate in the [discussion thread](https://github.com/cncf/enduser-private/discussions/86) for this architecture.