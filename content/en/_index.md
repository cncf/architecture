---
title: "Cloud Native Reference Architecture"
---

# Cloud Native Reference Architecture

Cloud computing, which we can think of as demand-driven delivery of IT resources over the network as distinct from statically delivered physical resources, allows and encourages changes in the way we deliver software. What, precisely, those changes are is not a settled question, and can lead to uncertainty when we try to design for the cloud from the ground up.

This site is opinionated about what "cloud native" means, but not about what technologies you use to deliver that vision. Here we define what we mean by "cloud native", and the associated examples show real-life architectures, used in major production settings, that implement some or all of these principles.
Examples also include the story of how they came to be to give you the organizational context essential to understanding the architecture.

To take advantage of cloud computing an application should be:

- Distributable, such that applications are built as loosely coupled services, each of which performs a single function. This supports horizontal scalability.
- Observable, such that requests crossing multiple services can be tracked through built-in monitoring, tracing and logging features to improve system understanding and reliability.
- Portable, such that applications can take full advantage of cloud computing by not being tied to specific vendors or implementations.
- Interoperable, such that services expose their functionality through APIs, allowing easy integration throughout the system.
- Available, such that failure in a service is handled gracefully with minimal disruption to the application as a whole.

The Reference Architecture site is a project led by the [CNCF End User Technical Advisory Board](https://www.cncf.io/people/end-user-technical-advisory-board/).

<p><img class="mt-3" src="/images/homepage/stage.jpg" alt="People discussing diagrams on a conference stage"></p>

## Contributing

Everybody is invited to suggest changes, additions, and improvements to the Cloud Native Reference Architecture site.
We employ a community-driven process governed by the CNCF to develop and improve upon this shared reference.
Contributions are welcome from all participants who abide by the project's purpose and charter.

Anyone wishing to contribute may submit a GitHub issue or create a pull request.

Please ensure you read the [How To Contribute](/how-to/) doc, join the [CNCF Slack](https://communityinviter.com/apps/cloud-native/cncf) workspace, and join the [#reference-architectures](https://cloud-native.slack.com/archives/C07JCV4CQD9) channel.

## Acknowledgements

The Cloud Native Reference Architecture site was initiated by the [CNCF End User Technical Advisory Board](https://www.cncf.io/people/end-user-technical-advisory-board/).
For a complete contributor list, please refer to [this GitHub page](https://github.com/cncf/architecture/graphs/contributors).

## License

All code contributions are under the Apache 2.0 license.
Documentation is distributed under CC BY 4.0.
