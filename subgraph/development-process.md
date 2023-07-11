# Development Process

{% hint style="warning" %}
All subgraph documentation is in development and not necessarily up to date.
{% endhint %}

Issues related to bugs and feature requests can be submitted on the [Beanstalk monorepo](https://github.com/BeanstalkFarms/Beanstalk) with a Subgraph tag.

1. Currently, a new branch is created for each release version. Any pending changes are made and commited to the new branch.
2. For initial development and testing, the subgraph is built and deployed to the `testing` deployment hosted by Beanstalk Farms.
3. Once the initial validation is complete and the subgraph can successfully index to chain head, the subgraph is then deployed to the `dev` deployment. From here other engineers can utilize this endpoint to update any items as needed (such as bots, UI calls, etc.)
4. Finally, given successful implementation on the `dev` deployment, the subgraph is published to both The Graph's decentralized network for indexing along with the `beanstalk` hosted deployment. An archive version is also created and supported on the Beanstalk hosted endpoint. For example, v2.0.3 is deployed to `beanstalk-2-0-3`.

### Beanstalk Subgraph Endpoints

**Beanstalk Farms Centralized Host**

* Production: [https://graph.node.bean.money/subgraphs/name/beanstalk](https://graph.node.bean.money/subgraphs/name/beanstalk)
* Dev: [https://graph.node.bean.money/subgraphs/name/dev](https://graph.node.bean.money/subgraphs/name/dev)&#x20;
* Testing: [https://graph.node.bean.money/subgraphs/name/beanstalk-testing](https://graph.node.bean.money/subgraphs/name/beanstalk-testing)&#x20;

**The Graph Hosted Service**

* Production: [https://api.thegraph.com/subgraphs/name/cujowolf/beanstalk](https://api.thegraph.com/subgraphs/name/cujowolf/beanstalk)
* Dev: [https://api.thegraph.com/subgraphs/name/cujowolf/beanstalk-dev](https://api.thegraph.com/subgraphs/name/cujowolf/beanstalk-dev)&#x20;

### Diagram

How the Beanstalk subgraph infrastructure works and where it is deployed.

{% hint style="warning" %}
This diagram is currently outdated—this warning will be removed when it's up to date!
{% endhint %}

{% @figma/embed fileId="djrEEVY4IBLEhPjeRTMteH" nodeId="0:1" url="https://www.figma.com/file/djrEEVY4IBLEhPjeRTMteH/[PUBLIC]-Subgraph-Deployment-Lifecycle?node-id=0:1&t=kNVlxPv4E2WH4ElL-1" %}
