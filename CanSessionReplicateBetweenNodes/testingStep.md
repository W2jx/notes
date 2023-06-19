
#### 1.Fetch the commits for debug in https://github.com/W2jx/liferay-portal/pull/184

#### 2.Build bundle.

#### 3.Run ant command in portal source root folder: ant -f build-test.xml cluster-session-replication.

#### 4.Setup a cluster environment with two nodes.

see https://github.com/W2jx/notes/blob/main/portal-cluster/create-portal-cluster.md

#### 5.Add portal property portlet.session.replicate.enabled=true to both nodes.

#### 6.Start two nodes.

#### 7.Deploy module portal-cluster-multiple-sample-web to node1.

> cd {your path}/liferay-portal/modules/apps/portal/portal-cluster-multiple-sample-web

> ../../../../gradlew deploy

#### 8.In node1, add a page and add portlet ClusterSampleSessionReplication into page.

#### 9.Check node1's log.