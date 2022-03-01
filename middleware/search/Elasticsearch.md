cluster - node - 

index - type - document - field
index - shard(primary) - shard(replica)

索引一篇文档
PUT <host>:<port>/<index-name>/<type-name>/<document_id>
{<document content>}

ES 服务
GET <host>:<port>

集群情况
GET <host>:<port>/_cluster/health?pretty

节点情况
GET  <host>:<port>/cluster/nodes/
GET  <host>:<port>/cluster/state/nodes/
POST <host>:<port>/cluster/nodes/_shutdown
POST <host>:<port>/cluster/<node_name>/_shutdown

文档
PUT  <host>:<port>/<index-name>/<type-name>/<document_id> {some-document}
POST <host>:<port>/<index-name>/<type-name> {some-document}
POST <host>:<port>/<index-name>/<type-name>/<document_id> {some-document}
GET  <host>:<port>/<index-name>/<type-name>/<document_id>
{_index, _type, _id, _version, exist, _source }
POST <host>:<port>/<index-name>/<type-name>/<document_id>/_update {some-document}
{_index, _type, _id, _version }
DELETE <host>:<port>/<index-name>/<type-name>/<document_id>
{found, _index, _type, _id, _version }

映射
GET <host>:<port>/<index-name>/_mapping

创建索引
PUT <host>:<port>/<index-name>

获取类型的映射
GET <host>:<port>/<index-name>/_mapping/<type-name>

搜索数据
GET <host>:<port>/_search?q=query
GET <host>:<port>/<index-name>/_search?q=query
GET <host>:<port>/<index-name>/<type-name>/_search?q=query&fields=a,b&size=1&pretty&timeout=3s
GET <host>:<port>/<index-name>/<type-name>/_search?q=<field-name>:query&fields=a,b&size=1&pretty

分析文档
GET <host>:<port>/<index-name>/_analyze?field=title

获取文档


