## Tabby
.\gradlew tasks
.\gradlew clean
.\gradlew bootJar

java -Xmx6g -jar tabby.jar

## Neo4J

### DB Settings
apoc.import.file.enabled=true
apoc.import.file.use_neo4j_config=false

dbms.memory.heap.initial_size=1G
dbms.memory.heap.max_size=4G
dbms.memory.pagecache.size=4G
dbms.security.procedures.unrestricted=jwt.security.*,apoc.*

### Initiation of DB
CALL apoc.help('all')

CREATE CONSTRAINT c2 IF NOT EXISTS ON (c:Class) ASSERT c.NAME IS UNIQUE;
CREATE CONSTRAINT c1 IF NOT EXISTS ON (c:Class) ASSERT c.ID IS UNIQUE;
CREATE CONSTRAINT c3 IF NOT EXISTS ON (m:Method) ASSERT m.ID IS UNIQUE;
CREATE CONSTRAINT c4 IF NOT EXISTS ON (m:Method) ASSERT m.SIGNATURE IS UNIQUE;
CREATE INDEX index1 IF NOT EXISTS FOR (m:Method) ON (m.NAME);
CREATE INDEX index2 IF NOT EXISTS FOR (m:Method) ON (m.CLASSNAME);
CREATE INDEX index3 IF NOT EXISTS FOR (m:Method) ON (m.NAME, m.CLASSNAME);
CREATE INDEX index4 IF NOT EXISTS FOR (m:Method) ON (m.NAME, m.NAME0);
CREATE INDEX index5 IF NOT EXISTS FOR (m:Method) ON (m.SIGNATURE);
CREATE INDEX index6 IF NOT EXISTS FOR (m:Method) ON (m.NAME0);
CREATE INDEX index7 IF NOT EXISTS FOR (m:Method) ON (m.NAME0, m.CLASSNAME);

:schema
:sysinfo