
  

# Intro to Data Engineering

Author: Daniel Beach

## What is a Data Engineer
- Data Engineers facilitate the movement of data , and enable businesses to consume that data
	-  **facilitate data movement**
	-  **enable data consumption**
- Other skills that enable you to be a **good** data engineer
	-  **knowledge and concepts first**
	- writing code second
- Chapters
	- Theory of Data Engineering and Principles
	- Data Pipeline Basics
	- Pipeline Architecture
	- Storage - Files
	- Compute and Resources
	- SQL and Databases
	- Data Warehousing and Data Lakes
	- Data Modeling
	- Data Quality
	- DevOps

  

# Theory of Data Engineering and Principles
- Build a solid foundation reduces downstream headaches
- The foundational principles directly impact code and technology decisions

### What is a Data Pipeline
- moving data from point A to point C, with a transformation B in the middle
- a **good** data pipeline:
	- facilitating the **movement**, **storage**, and **access** to data in a **repeatable**, **resilient**, and **scalable** manner

### Data Engineering Standards
- Pipelines conform to the same level or higher expectations as normal Software Engineering
  
### Movement
- by definition: picking up data from somewhere and dropping it off at a "home", with some number of stops in between
- common movements:
	- streaming data (real time)
	- batch processing
	- micro-batch processing (near real time)
	- ETL/ELT
- types of basic approach to data movement is critical: all downstream actions are most likely very different based upon the answer of streaming vs. batch
- technology choices affect code and architecture

#### Complexity in Data Pipelines
- data engineers should reduce complexity
- code is probably a pyramid of complexity
- foundational decisions made upfront will direct the type & scope of the code that is needed to implement the rest of the project
- don't over engineer solutions

### Storage and File Types
- Storage affects both time and money
- Data rest (file) storage affects technology and code access patterns
- many of the file storage choices can be hard to back out of once baked into the software solution

#### Storage and Files affect Technology and Code
- consequences are large and requires a sizeable project to regain insights into the data that could have been avoided by proper storage upfront
- storage can be seen as just as inconsequential decision when building data pipelines - rarely the case as the project gets popular and starts to scale

  

### Access
- the data output from a pipeline or intermediate steps should be easily and quickly accessible
- how do people/machines consume the data in question
- data is of no use without reasonable accessibility and usability
- ** data access patterns, and their variety, drive engineering solutions**
- how the data will be access and explored
- how and where the data is stored at rest
- presented for use by consuming users/applications

### Repeatable
- anyone must
	- run a pipeline
	- be able to troubleshoot a pipeline
- pipelines break, they will have to be rerun
- pipelines should produce the same results > **idempotent**

#### People and Assumptions Affect Pipelines
- anyone should be able to clone the repository, look at the README, with a few lines of code, kick off the pipeline
- shouldn't take more than one button click/command line argument to restart/run any data pipeline
- should not be a myriad of configurations, flags, and files that must be staged in certain ambiguous places for the data pipeline to run

### Resilient
- codebase must be written in such a way that it isn't fragile
- should not be many instances of hardcoded values [dates, numbers, etc.] in the code
- when data pipelines break everyday, it signifies fundamental problems
- resilient pipelines require attention to code and architecture
- good data pipeline:
	- specific enough to get the job done efficiently
	- not so specific that minor changes in requirements don't lead to codebase rewrites & refactors at every turn
	- ** thinking ahead, without overengineering a solution**

### Scalable
- data pipelines should be built to handle more data
- common problems: scalability issues leading to poor performance
- rarely write a pipeline to deal with one piece of code and have it scale up without significant changes

# Data Pipeline Basics
-  **best principles start with a solid foundation**
	- project structure
	- testing
	- documentation
	- containerisation
	- architecture first

### Project Structure
- be short and to the point when writing code
- data should flow through the code in an obvious and human readable way
-  **build on a solid foundation**
- can't have good ppipelines without a solid base
- have to do the small parts well to make the whole project better

### Data Piperline Code Structure
- start with `main()`
- every pipeline should start with a `main.py` and a `main()` function
- always include a `main()` entrypoint for data pipelines
-  **good coding practices make good data pipelines**
	- mindset of clean and concise code structures that are easy to read ans use
-  **code should flow with the data**
	- should continue pattern of obvious code and data flow
	- pipeline code should follow the data flow in a sense
	- methods & functions should be named to indicate what they are doing and should be called inside `main()` method in an obvious pattern
-  **don't focus on the details right away**
	-  help us think about how scalable, efficient, and extensible the pipeline will be 
- Code Readability and Organisation
	- every `main()`function should show the flow of the data through the pipeline in an obvious fashion
	- if the different stepd you will be designing thorughout the pipeline requires 5 or more functions, should consider breaking those out into a separate python class/file
	- makes the code more reusable, maintainable, easier to debug
	- gives context and doesn't overwhelm someone else/debugging/feature additions
	- don't have the bad habit of writing data pipelines all in a single file
	- break up functions into the smallest units possible
	- write data transformations that are re-usable
	- avoid long functions and methods
	- functions and methods that are working on data and contain too many lines are going to be prone to error and impossible to maintain or troubleshoot

### Tests
- need to have tests for every data pipeline
- tests are basic to data pipelines
- protect pipelines from bugs and errors
- increase development productivity
-  **unit test**
	- changing the business/transformation logic acting upon data should be tested in such a way that anyone can attempt the change and run tests with a reasonable assumption that unit tests will catch any problems
	- not a good idea to wait until you're done before thinking about tests
	- many times writing unit tests for the method/function will cause you to refactor code to make it simpler/more testable

### Documentation
-  `README.md` is your chance to get the important ideas across
- give a high level description of what the code is doing
- describe the input and output datasets, where they come from and where they go
- list any reasons and business requirements that drive decisions when writing code
- explain how to test and deploy the code
- talk about any configurations or other arguments used in the code

### Containerisation
- no easier way to make data a pipeline and reliable than to have a Dockerfile to run the code on
- removes all system ambiguity
- containers are a great equaliser when it comes to systems, requirements, dependencies
- essentially freeze every detail about where and how the code runs
- accessible to yourself/anyone coming on later to work on the project
- anyone can run/test the code
- reduces the chances of code/packages breaking the pipeline
- integration is easier > today's distributed systems are embracing containers
- clear from Docker container what tools and tech are begin used
- all packaged and ready to go > no manual installations

### Architecture First
- diving into writing code right away without working through the architecture first is a big mistake
- architecture before code always
- think before act or write code
- ask questions early and often
- **pipeline architecture start with questions **
	- a thought process the begins before a single line of code is written and that usually where projects live or die
-  **typically when a project or codebase starts with a mess of files and no project structure it sets a precedence that the code is no good either**
	- tech debt and bad design happen when you say "will fix that later"
	- being messy with project structure upfront will ensure things only get worse
	- when tests are not a first priority of data pipelines, it ensures failures
	- not taking the time to containerise the project with Docer makes development difficult
	- skipping architecture even on simple projects is a mistake

# Pipeline Architecture
- about the big picture
- fitting puzzle pieces together
- reducing complexity
- finding the right tools for the job
- making tradeoffs
- allow the data pipelines to flow free and fast
- ** the best architects use their knowledge, experience, and research to understand the technical details of what has to happen**

### Architecture applied to data
- business requirements
- end result is needed
- service level agreements (SLA)
- draw it before you write it
- how much data, how often, how quickly will it grow
- storage and compute needs
- what pieces of technology fit the requiremtns best
- what do I have today that will do the job, what are the tradeoffs
- code architecture > how it should be implemented
- batch vs streaming
-  **avoid swinging too far into over-engineering a solution**
	- architecture provides space to think and plan
	- space to faily early
	- simple over complex
	- think about connections between systems
	- think about coupling or connection between systems, or pieces of the pipeline
	- the tools must work together
	- such concerns are to be considered during the architecture planning phase of most data engineering projects

### Examine Requirements
- examining the requirements of the business or as much of then as you can get
- understanding what the final exceptions are is key to making technology and pipeline design decisions
- always understand final output and expectations
- understand current and future infrastructure

### How much data, how quickly will it grow/types of data formats
- where should the data be stored >cloud/local
- what type of tech platform is good for this type of data
- calculate rough data sizes and speed of processing needed
-  **in architecture planning > break down what we know into bite-sized chunks, ask questions, start making estimates and design decisions based on what we do know**
	- realistic in when architecting data pipelines
	- context is important
	- drawing out the current state and proposed future states is helpful
	- calculating rough data size and usage helps us making decisions
	- cost of storing our data in the cloud is known with rough size calculations

### Review architecture problem
- having a good step back and thinking through the data flow and requirements is critical step to not ending up with an expensive over-engineered solution/simplistic solution that breaks later because of failure to scale
	- calculating data size and velocity
	- calculating compute/storage requirements based on data size
	- understanding the end results
	- complexity vs simplicity tradeoffs
	- understanding cost

### Data size and velocity
- calculate rough data size and velocity requirements
-  forces a basic understanding of what the data looks like and potential issues
	- understanding the velocity or incoming volume will shed light on what are and are not acceptable solutions
- size of the data and velocity/frequency of the data should impact the architecture
- data size
	- what format is the data coming in
	- can we simply mick-up a sample file ourselves
	- what types of systems handle data files of these size?
	- **size of the file is also going to tell us generally about what type of technology is best suited for this particular problem** 
	- **think carefully about which technologies would be best suited for the size of data your pipeline is handling**
- data velocity
	- amount of incoming data (velocity) is another critical aspect of data pipeline architecture
	- at what rate and frequency is the data coming to us
	- some architecture and tools are better suited to high volumes of data then others
	-  what some fo the rest of the pipeline might have to look like and handle
	- **calculating data size and velocity upfront, even if end up being half wrong is incredibly helpful**

### Calculating compute requirements
- amount of compute that will be required
	- number one driver of cost
- the more compute power that is needed the more expensive the pipeline will be to run
- with rough data sizes, break the work up into logical batches
- determine based on transformations and possible tooling, the required CPU and RAM
- **resource requirement = (processing unit size x (number of CPU + RAM)) x number of batches **
	- can use rough resource requirements to size machines and clusters

### Calculating storage requirements
- same as compute resources
- once you know this information likely with some compression numbers that are not hard to find, cloud storage costs and be found out
- going through teh exercise of understanding roughly the storage and compute requirements might change our architecture decisions about what tools to use and our approach to the problem

### Understanding the end result
- trying to think about the result
- **step back and understand where the data is going to be & what it needs to look like**
- **end results will often change the way we get those results**
- getting a clearer picture of the output and usage of the data needed from the pipeline will inform or change some of the choices we make upfront
	- impact on what tools we choose to process and output that data
	
### Complexity vs simplicity tradeoffs
- **complexity id the silent killer that sneaks up on you**
	- extended debugging and error research times
	- extended development time to add new functionality
	- extended period to onboard new developers
	- developers are afraid or unwilling to touch code
	- high cost of running and maintenance
- overly simplistic solutions have their own set of problems
	- developer boredom and short tenure
	- inability to scale 
	- cannot extend the functionality
	- extended time to develop and add new functionality
	- stagnation of technology stack
- choosing new tools and technology simply because they are new is a bad habit and happens too often
- **let the data and requirements drive the complexity, not the other way around**
	- take a pragmatic and balanced approach to solve the problem
	- too complex and the pipeline will be unmanageable
	- too simple and the pipeline won't scale
- reasons to incorporate simplicity and complexity depending on the situation

### Understanding cost
- understand the size, volume, and types of data that will be coming, along with what technology choices are likely to be the best fit
	- figuring out the cost is usually not that hard
	- understand the data file/record size will affect cost
	- understand that the volume of the data will affect cost
	- your chosen tech stack will affect cost
- **knowing the size and growth of storage requirements, along with looking at pricing documentation**

### Code Architecture
- approach your data pipeline code cautiously and slowly
- plan at a high level before writing code at the low level
- keep functions and methods as small as possible break code into logical units
- stock to normal software engineering best practices

### Batch vs streaming architecture
- pipeline will either be batch or streaming
- distinction should be made early in architecture
- streaming
	- ingesting high volumes of high velocity and relatively small data points
	- Kafka, Pulsar, Spark streaming
	- popularity of microservices
	- data isn't very flat or relational
		- fits JSON structure better
	- **high velocity of data**
	- **smaller data record sizes**
	- **increases complexity of pipeline architecture**
- batch
	- real time isn't that necessary, data points produced in batches/together, in a very flattened and as a file
	- **batch data pipelines will be working on ingesting files, streaming will be working on individual messages/data points**

### Review
- **understanding how storage solutions word together with data transformations and analytics tools, and how those tools work with orchestration tools, these types of decisions  are what architecture is really about**
	- number of technology choices available can make architecture difficult
	- try to break down problems down into its pieces
	- always keep the big picture in mind, not every detail

# Storage
- pipelines typically start as some sort of file, and the result usually ends up as a file
	- there are some commonly used file types across all data engineering
	- understanding the pros and cons of different file types are important
	- storage plays a large role in big data
- why care about storage
	- **decisions should be driven by the data needs and access patterns should be explored before just "picking" something because its easy**
	- **productivity and speed gains that can be found in properly picking file storage and partitioning strategies**

### Access patterns
- how files need to be read and searched by our data pipelines & those systems that ingest the results of data pipelines
	- how many systems will need access to the data storage layer
	- how often will be above systems be accessing the data storage
	- how much data will these systems be reading
	- how much logic will be applied by those systems to the data
	- how does the system technically access the data
- access patterns at a high level
	- data will need to be accessed via a database
	- data will be accessed via a file storage
- include how much of the data will be accessed at one time
- **having a storage system that supports fast single lookups vs serving requests will have how we think and choose technology**

### SQL/NoSQL databases vs files
- rules of thumb you can follow to help make the decisions
	- is the data tabular and relational
	- data volumes, ingress and egress
	- is the data of key-value or ragged structure
- data storage considerations
	- fit into multiple tables that have very straightforward relationships together
		- can be easily represented in a spreadsheet
		- **tabular and relational data should go into SQL databases**
		- **high ingress and egress volumes of data might not suit many SQL databases**
	- is data best modeled by a document
		- documents that are very relational and transactional are also great candidates for NoSQL
		- if the data needs to be more on the analytical side or the transactional support side
		- data that leans more into the key-value pair model, with possible built-in hierarchical ragged structures are prime for NoSQL data stores

### How to make storage decisions
- evaluate which technology best fits the need in a manner that is simple and supports a reasonable expansion of requirements and data
- any sort of requirement for supporting transactional systems from web apps to manufacturing systems where CRUD and ACID reign supreme
- traditional database storage has given way to the feature-rich file storage solutions

### File types
- files have become the defacto new data lake
- **type of file chosen as the storage layer has a massive impact on data pipeline performance and usability**
	- data compression
	- smart files (predicate push down support, selective reads)
	- file type usability by ingestion systems and code
	- schema and data type support
	- row and columnar storage
- **data engineers need to understand high-level file storage options and what use cases warrants the use of each file storage options**

### Row vs columnar storage
- row based storage stores data in rows next to each other, like you would visualize data normally in your mind
	- makes for quick writes (inserts) and reads on those rows of data 
- columnar storage stores the data field or column wise
	- data from different rows but the same column/field is stored adjacent to each other
	- makes queries and computations much faster
- **row based > quick insert and reads**
- **columnar > analytics and computations**
- traditional data warehouses or data lakes patterns designed for analytics computations would fall into the columnar storage systems
- high volume transactional data being streamed from a clickstream would make more sense as row-based storage

### Common file types in data engineering
- **parquet**
	- probably the most popular columnar storage file type
	- schema/data type with the file
		- great compression
		- predicate pushdown (filter pushdown, read what you need)
		- selective reads )only read what you need)
		- support  across platforms (spark, pandas, etc)
		- ease of partitioning
	- parquet schema and data types
		- string, int, decimal/float, boolean, binary
	- parquet compression
		- gzip, snappy, LZO
	- parquet predicate pushdowns, partitions, and projection reads
		- ability to only read the data you need
		- **reading select columns from data sets is a game-changer for big data**
		- specify what column you are interested in working with
	- parquet partitions
		- many times parquet files are partitioned into subfolders based on some column, usually a date
		- breaks the dataset up into smaller chunks
		- rare to have parquet datasets that are not partitioned
	- predicate pushdowns
		- reading the dataset with filters that are "pushed" down to the file can create huge performance gains over file formats like CSV that don't have this feature
			- **can quickly read data that meets filters**
- **Avro**
		- data serialisation framework
			- being able to handle flexible and wide-ranging data structures (even hierarchical records)
			- handles schema changes
			- row-oriented
			- ragged schema structure support(similar to JSON)
- **Avro vs Parquet**
	- avro format is used widely in the RPC (remote produce call) space 
		- communicate messages and data across networks
		- **avro is going to be found in more highly transactional and messaging systems and architectures**
		- schema is an integral concept
- **orc**
	- ORC files are made up of Stripes (groups of row data)
	- supports data types like "datetime, decimal, and the complex types [struct, lists, map, union]"
	- file has/can have "indexes"
		- helps in seeking rows and skipping row groups when a reader comes in with a predicate (push down filter)
		- file footer contains meta-information about the ORC file as a whole
	- stripes and indexes for ORC
		- 64MB in size by default, are "independent" from each other
		- allow distributed work to happen on a file
	- columns are separate from each other in the stripe, allowing only needed data to be read
	- allow push-down read filters into a file
	- designed for HIVE and will most likely not run into it unless working on legacy systems
	- choose parquet over ORC
- **CSV/ flat file**
	- most common file format used in data engineering
	- easy and simple to use
		- as simple as they come
		- don't hold schema or data type
		- delimiters matter with these files
	- text files with some sort of separator between records, typically a comma is used
		- isn't uncommon to double-quote records as well
		- no compression
		- data values are separated by a comma, but also pipe, and other values
		- no schema or data type support
		- many times datapoints will be qualified, may be surrounded by quotes ""
		- very easy to read and write in most languages
	- **pandas for CSV and flat files**
	- **probably the easiest storage optino, work great for data that can be represented as a table, with rows and columns
	- provide no out of the box compression options
- **JSON**
	- used for configuration and not as the main storage type
	- best for ragged hierarchy schemes
	- contains list and arrays, as well as depth into its schema
	- **should not choose JSON if storing large amounts of data into a storage bucket**
		- JSON don't provide partitioning, predicate pushdown, compression of other file formats
	- great tool for storing configurations for applications, as well as messages and individual data objects being passed around inside a data application
	- if data is more document oriented

### Compression
- gzip, tar, snappy, zip
- when storing files there should rarely be the case where those files are not compressed in some manner
- saves size and money
- there isn't much of a penalty to uncompress those files on read
- storing and warehousing large amounts of data
- makes sense for cost reasons alone

### Storage location
- high availability and access from anywhere is pretty much standard operating procedure
- no more network mounts and drives to mess with
- ** have to learn and become adept at using the command line interfaces provided by the cloud providers to interact with their storage systems**
	- learn the command line CLI tools for cloud providers
	- cloud storage locations are the future
	- costs money to read and write from the cloud
- learn the packages and libraries provided by the cloud companies
- reading and writing massive amounts of storage is going to increase storage charges and cost

### Partitions
- **how the data files you are working with are physically stored and organized on a disk or in the cloud**
- makes it easy for people and for code to find data
	- partitioning keeps programs from reading entire storage dictionaries
	- partitioning breaks the data up logically and physically
	- partitioning increases performances and reduces cost (less read)
- **why you need partitions**
	- when you have petabytes or terabytes of data
	- can't read every file when a pipeline needs some data, that would take too long and make the system unusable
	- allows for more fine-grained file system seeking data locating
	- grouping data and saving it in partitions is at the core of big data

### How to think about data partitioning
- same thought process should be taken when thinking about data organisation
- trying to understand how data is either produced and consumed and applying some common sense organization around that data to help both humans and software work with that data
	- data partitions are based on data access patterns
	- common items in classic WHERE clauses turn into partitions
- data partitions can get very complicated and they might be certain nuances to consider when working with specific tools
- organizing data and files into common sense patterns

# Compute and Resources
- **managing the resources and compute available is the key to a pipeline that is efficient and fast**

### Overview
- RAM, CPU, Storage, Cluster/Mode
	- affect how fast the code runs, how much data is processed
	- resources affect pipeline
	- how much data we can process
	- how much money we pay to run our pipelines

### Managing compute and resources
- how we can generally approach compute and resources in a semi-structured way
	- what resources are available
	- what does the tech stack require for resources at a minimum
	- how to reduce resource consumption at a minimum
	- how to maximise the resource usage based on what's available
- **find out exactly what resources are available on the platform in which the ETL will be running**

#### How to handle resources
- should do everything in power when writing ETL and code to use every last scrap of RAM and CPU
	- concurrency(how many things can you do at the same time)
	- in memory (how much data can fit into memory you work on)
- ** need to find a way to process more  files concurrently, user every last CPU and RAM to chew through the files**

### RAM/Memory
- data engineers: transform large amounts of data via pipelines
	- how much memory is available
	- how much memory needs to be left available for the operating system
	- at tis peak, what will the program's max memory usage be
	- can calculate memory consumption based on data
- calculate the size of he data file/ piece of data the you're working on
	- compare to the size of resource and do simple division to see how many pieces of dat you can fit into memory
- memory is faster than disk
	- working on data in memory is much faster and is a great option to use when available

### Intro to StringIO and BytesIO in Python
- great features for maxing out memory usage
- IO streams are underused feature that rarely come up in most code bases
	requires us to think about RAM and how much resource is available in our machine
	
#### What data engineers work on
- reading and writing files to disk will be a bottleneck in programs
	- especially if reading and writing the same file multiple times

#### BytesIO and StringIO
- in memory data objects
	- act as a File Object
- treat and interact with these objects like you do any other file
	- have a File API on top of them
	- IO streams are streams of dta
	- they have File Object (read/write) type features
	- help get used to thinking about RAM/Memory s related to code
	- faster than disk operations

### RAM/Memory Review
- data in memory is going to be faster than dta on disk
	- data pipelines that work in memory are much faster
	- working with data in memory can cause OOM issues
- RAM is fast and useful
	- limited and easy to run out of

### CPU/ Cores
- probably have a few cores
	- leaving those cores unused is a waste that could significantly reduce code run times when used properly
- **use all the CPU./cores available**
- **increase performance with the increased use of CPU**
- **understand what type of code requires more CPU and what doesn't**
- must be balanced by how large the files are
	- if we start reading more than one file at a time, we should be aware of the available CPUs and memory on our machine so as not to overload the system
- break down workflow into basic parts
- start by understanding the "unit of work"
- try to understand how to "spread" up the work across different CPU
- **breaking down a large task into its components**
	- figuring out how you can spread the workaround to multiple cores

### Storage
- most servers and resources come with either a set amount of storage attached
	- possible some elastic storage that is quite large, or pipelines will just read & write directly to the cloud
- not cleaning up after yourself or knowing upfront what disk space is available is a good way to get into trouble
	- always knowing how much disk space is available on your resource
	- if you write to disk, always clean up after yourself
	- reading and writing directly to cloud storage is best but creates network bottlenecks

### Cluster/ Nodes
- understand the system and resources you are working with > **what you have available**
- depend on the number and size of the workers available to process data
- save you from wondering why a pipeline is running for more than 1 day or gets OOM errors

# Mastering SQL
- SQL is still a major player in data engineering
- most of the popular data engineering frameworks (Spark) support SQL
- tuning queries, writing queries, indexing, designing data warehouses
- does the type of database matter
	- fundamental SQL skills transcend database brand names
	- **type of RDBMS doesn't matter to learn SQL database/fundamentals**

### OLTP vs OLAP
- OLTP: highly transactional in nature
	- wide and few, made to ingest data quickly
	- wide columns designed to handle high volumes of inserts
- OLAP: analytical in nature (data warehousing, aggregation)
	- star schema, some aggregate tables with many connected dimensions
	- designed for summarising and aggregating data

### Table design and layouts
- "normalising" a table is about data de-duplication, and the extent that you can take that concept into table designs
	- normalising tables aims to de-duplicate, ensuing integrity, and logical data management
	- normalisation can be taken too far
	- be logical in breaking up data into tables
- **easiest approach is to group datasets into their logical units**
- concept of database and table normalisation if plan to work in/around classical relational database and data warehouse environments
	- don't let tables get too wide
	- table designs usually follow the logical business units closely
- have to know the queries first
- break up the data into logical units
- don't put everything into one table

### Primary keys in table design
- easily list what columns make a row of data unique or different from all the other rows
	- define what makes each row of data unique
	- uniqueness can be a single column or multiple columns
- break the ides down logically
- think about the relationship between the logical units
- **keep it simple**

### Understanding indexing basics
- every table needs a primary key (uniqueness)
- every table probably needs secondary indexes to support queries and joins
- don't go overboard
	- indexing too much can have negative impacts
- table join keys should be promary and the most important index
	- columns that show up in GROUP BY and WHERE clauses should be in indexes
- **understanding the queries that will be used on the tables, especially the WHERE and GROUP BY columns**, indexes should be created to support those

### How to write fast/tune queries
- think about SELECT
	- never do SELECT *
		- wastes resources and can double/triple the size of datasets that don't need to be that big
	- no subqueries in SELECT statements
		- don't put subqueries in SELECT statement, requiring it to be run for every row
	- make a WHERE clause as big as possible
		- add more things to WHERE clause
	- views are bad
		- always drag down the performance of queries
		- can be useful and used well - but try not to use
	- save the details for last
		- aggregate first, put details later
	- user defined functions work well as views
		- functionality within the stand functions of the database to get the answer you need
		- without running a UDF
		- UDF have to run for each row - gets slow fast
	- break down queries into logical units

### Data types, especially of join columns
- joining on keys that are intergers is going to be much quicker than a string hash that is 24 characters long

### Summary
- try to use DQL that applies to the entire dataset
	- GROUP BY, WHERE
- instead of using UDF or a SELECT in the SELECT statement

### Where to look for common problems
- check the indexes
	- are you joining some other column with no index
- are the index stats being updated
- look for bad SQL
	- do the joing and subqueries look reasonable
- inspect the complex parts of the query
	- if something is complex it's probably like that for a reason
- learn how to read query execution plans and stats

### SQL fundamentals
- **SELECT** statements
	- only ever SELECT the columns you need
	- avoid putting complex logic in you SELECT statements unless necessary
	- its common to put CASE statements in the SELECT
	- avoid putting complex logic in SELECT statements
		- usually means that logic must run on each row individually
-  **JOINS**
	- INNER 
		- only matching rows joins
	- LEFT or RIGHT OUTER
		- keep only those records that have a match in one or the other
	- FULL
		- give everything on both sides
	- ANTI JOINS
		- give records only found in one side or another
- ** GROUP BY** and **WINDOW** functions and **AGGREGATE** functions
	 - would only have GROUP BY or use a WINDOW fucntion when aggregating or working on some subsets of data
	 - most data queries written by engineers will require some GROUP BY or WINDOW functions, usually in combination with some aggregate function
 - **WHERE** clause
	 - any filtering or subsetting can be done with a WHERE clause, as early as possible in the process
		 - ensure best performance and run time of a query
	 - figuring out WHERE clause also typically give great insight into how the data should be indexed or partitioned
	 - advisable to spend time understanding common WHERE clauses and filters while a data model is begin built before anything goes to production

### SubQuerys and CTEs
- ** CTE**
	- defined with the WITH x AS (...) syntax
	- are a temporary result set
	- can be thought of as a temporary table
	- can be referred multiple times in a query
	- encapsulate logic as code
- **subquery**
	- powerful way to slowly and methodically build up complex queries and logic
		- correlated
		- uncorrelated

# Data Warehousing/ Data Lakes
- many of the same concepts still apply when designing classic RDBMS data warehouses or Data Lakes in the cloud/S3

### Data Warehouse vs Data Lake vs Lake House
- data warehouses are known to be strict Kimball or Immam style schemas
- data lakes start to blur the line and are less strict
	- data warehouse/lake/house are usually defined differently by different people
	-  kimball star schema design still very popular and useful
- supposed to be the single source of truth to which all data flows and is captured
- data model applied
	- **data model (many times driven by underlying technology) is the main difference between a Data Warehouse and Data Lake**
- data warehouses and data lakes are there for OLAP (aggregation purposes)
- comes down to how the data is stored in its "tables" and what the relationship looks like between the different data sets
- both seek to at minimum de-duplicate data, clean it, store it logically, many times capturing the historical versions of that data as well (SCD)

### Facts and Dimensions
### Fact Tables
- central dataset that grows the quickest and is used to aggregate data
- have some sort of date or time series associated with them and are transactional in most cases
- data in a Fact table could also be known as an "event"
	- a record that something happened
- naturally summarised or aggregated

### Dimension Tables
- datasets that help describe and extend information in a Fact Table
- help understand and interpret certain values in a fact table
- primary goal is to be used as a "look up" table
- a good fact table in a data warehouse should consist of some nondescript ids (date) and values you would want to aggregate on

### Constraints and Schema
### Constrains
- data warehouse/lake > ability to enforce rules upon data from various sources
- gives the ability to expect uniform values in the most critical data points
- file-based storage systems like Delta Lake support constraints
- different constrains are supported in different systems
- common constraints
	- NULL/ NOT NULL
	- CHECK (a value in some range/meets certain criteria)

### Schemas
- ability to control and enforce column names and data types
- trying to take data points that are different and somehow commonise then into a single store from which can answer any question
### Data Types
- define all the data types you expect for each data point before hand
- mixing of INTEGERS with STRINGS will cause major issues that need to be fixed downstream
### Column Names
- change of column names over time
- nothing is more confusing than the "same" data source with different "versions" if data
	- introduces complex transformations and logic that has to "combine" datasets so a full view can be taken of the dingle data source

### Role of ID's in a Data Warehouse or Data Lake
- **critical to understand that the data repository that is the central hub of truth for an organistion needs to be just that - the source of truth**
### Uniqueness
- data in the Lake/Warehouse is going to be de-duplicated and somewhat transformed
- can't de-duplicate and have unique data records without having keys (primary or otherwise) that identify our data
- done by ids either in a SQL table or as hashes generated by code in a Data Lake
- difference between data dumped into cloud storage and a Warehouse/Lake
	- Warehouse/lake: take time to understand and transform the data into a unique and usable dataset that can be related to other datasets easily
-  **being able to identify every Fact and join to Dimension on ideally a single column will require an id to be generated during the creation and loading of Data Warehouse/Lake

### Relationships
- **keys/hashes we use in our table structures to uniquely identify each row**
- need to be able to JOIN datasets together, without producing duplicates in Data Lakes
- most business requirements require datasets to be joined to derive deep analysis that provides the best insights and answers
- **much time should be spent no defining the relationships between data tables and stores**

### CDC/History Tracking
- effective start and end dates/times
	- effective start and end times of a record provide a great history of tracking what happened
- active flag
	- if you just want the "current" snapshot of what is more recent > can simply add a WHERE or FILTER to say `active_flag=1`

### CDC implementation notes
- need to break up source records into two groups
- get the records in the source that ARE NOT in the target
	- becomes INSERT new records
- get records in sources THAT ARE in target
	- UPDATE records in the TARGET to set "end" or "stop" datetime and turn OFF the active flag
- simply a matter of ending the records (UPDATE) in the target that already exists
	- inserting new records

### TLDR
- **facts and dimensions**
	- don't go overboard with normalisation
- **constraints and schema**
	- placing constraints and the correct data types in schemas of a data warehouse/lake will save time and trouble
	- validating inputs and commonising the data to be the same key part of what a data lake provides the value
	- put value constraints in at high-value targets, columns, and find them in WHERE clauses or filters

# Data Modelling
- data model should reflect how the data is going to be used
	- should reflect that need and provide a schema for the data that can support such needs
- understanding the schema > made up of data types and definitions
	- **each piece of data should be assigned a data type, constraints around that data, and, a definition, including a name**

### Data Types
- basic data types don't change very much
- data types specifically will change slightly if you're using Postgres vs a parquet file
	- will be using some sort of string or char, int or decimal, true & false boolean values, sometimes array or list, or other more complex types

### Data Types
- consider data size when defining what data type should hold which data points
- don't wan't to waste a lot of space by calling every column a `STRING` just to make things easy
- data can add up over time
	- choosing the correct data type for your data points will have a large imapct on storage size
- easy to fall into the trap of just glossing over data types, assigning certain values to `STRINGS`
	- or not understanding `DECIMAL` points involved in a numeric column
	- even understanding if `INT` is a `BIG INT` or not

### Constraints
- understand the constraints that surround each data point
- **having robust constraints around your data is the first step in data quality**
- constraints are a great way in either Data Warehouses/Lakes to control the wuality and ensure the integrity of the data being stored
- catching problems early can be accomplished easily with constraints 
	- think of constraints as your first line of defense

### Constraints for numeric columns
- constraints can check to make sure a value is in some range of sanity
	- a great way to ensure mistakes in source systems don't cascade farther into other parts where they are harder to extract and correct

### Constraints for string columns
- ensure the filters and where clauses will work
	- constraints can catch spelling and typo errors

### Data Definition
- having a definition of the data points is a two-fold task
- readable column names that carry meaning as well as description of data points
	- legible column names with meaning
		- define column names that tell someone what the data point is without too much problem
		- simply reading a column name should tell you a lot of what you need to know
	- descriptions
		- should be kept for each data point
		- easiest to dow ehn creating the schema of the data first
		- putting together documentation or comments in a codebase will come in handy later
	
### Modelling data logically
- **logical data modelling is grouping sets of data that logically should be together**

### Logical data models lead to physical relationships
- gives a sense of the type of information that will be available
	- even the relationships (join) between the different groups of data
- once broken data sets into logical units, `JOINS` between those data sets start to present themselves to the designer
- good starting point for talks and reviews with businesses and stakeholders about the data needs and think about how the logical model could answer these questions
	- makes the most sense to a nontechnical audience
- great tools for documentation when introducing new technical engineers to a dataset

### Grain of data
- **the grain of data is the lowest level of information available on a topic**
- if you design a data model that relies on an Orders table having only a single line for each order
	- a summary of multiple items
	- later realise that you are missing important information that can only be obtained from a "lower" grain of data
	- need a data record for each item ordered
- knowing the lowest level of information that is required by the business logic and requirements that are driving the data model is important
	- **identifying the lowest level of grain should be one of the first tasks when data modelling because it directly affects the final schema of the data model**

### Uniqueness of Data
- each table or data sink you are trying to design and model should have something that uniquely identifies each record or row
	- identify each record
	- helps with `JOIN` relationships
	- reduces the duplicate row problem
	- many times uniqueness is a combination of multiple problems
- if unable to identify what makes a piece of data or row, likely don't understand enough about the data
- uniqueness factor of the data will tie directly into what are the primary keys that will eventyally be needed for each record, or join later
-  failure during the data modelling process to identify for each logical group of data
	- what makes each record unique
- typically a combination of data points, sometimes even combined with date
- what makes the data unique and what information might have to be added to make a record unique
- every join to other data source starts to compound the problem
- once duplicate records are placed into the system they are typically painful to back out and remove

### Access Patterns
- difficult to ascertain at the beginning of a project when a data model is taking place
	- understand queries 
	- how downstream systems consume the data
	- understand business needs and requirements for the data
- how teh data is queries and used in the end
- can be sometimes hard to know exactly what type of queries will show up, and how the data will be used
- can at least get a decent idea by talking to the downstream people and applications that will be using your data and data model

### Talking to the business
### Business requirements impact the data model
- most of our data is going to be aggregated by date and produce and customer
- data values become prime targets for indexes or partitioning strategies on technical stack
- **thinking about the columns and data points used in `WHERE` and `GROUP BY` clauses is key for data modelling correctly**
- if don't understand how the data is going to be used there is a good chance the data model wont' support the queries and access patterns that try to use that data source
- problems: performance and difficulty retrieving correct data with reasonable logic

### Normal forms
- can loosely follow the level of data normalisation or de-duplication and benefit from much of what they provide in a file-based data lake
-  de-duplication of data
	- one of the main tenants of normalisation > the removal of redundant data is integral to data models of all kinds
- join integrity
	- understanding how different data sets related to each or the joins
	- part of normalising your data is controlling how these joins occur and the type of results they will give back 
	- think closely about the data model and how these joins will affect everyone and every query downstream

### Keys: Primary and foreign
- relational databases support the concept of primary and foreign keys
	- many new data lake technologies (Delta Lake) don't

### The idea behind keys
- **doesn't matter what are the underlying technologies is beneath the model, the fact is that the data is only useful enough as far as it can be reliably related to other entities**
- understanding how each table or sink of data can be related to others, and how that "join" would function is critical to any data model

### Generate own keys if you must
- isn't any official implementation of a foreign key that is enforced
	- doesn't mean that you shouldn't design a key yourself that acts as a foreign key
	- actually a good idea
- having a key in each entity that can be used to relate to other entities easily will force better practices and long term results and data usability
- requires a deeper understanding of data sources
- exercise of designing keys will make you the subject matter expert and result in a better data model

### Relational Databases (SQL) vs Data Lake (File Based)
- SQL models:
	- many dimensions, data norms, and de-dups to the extreme
	- table sizes doesn't matter: small or big
	- centered around indexing and indexes
- File-based models:
	-  fewer dimensions, normalisation in moderation
	- table size and file size matter in the extreme
	- data models are centered around partitions and partitioning
	
### Number of fact tables and dimensions and normalisation
- relational SQL databases blazing fast and joining many small tables is no big deal
- data deduplication and normalisation were taken to the extreme in these data models
	- fit the technology

### File size and table size matter int eh new file-based Data Lakes
- small file sizes and small datasets can wreak havoc on those tools
- technically most big data tools get slow when you start to include large number of small files or datasets that have to make their way across a distributed cluster network and disk that is behind those big tools
- hundreds of TB of data can be scattered across many hundreds to thousands of nodes depending on workload size

### Partitions vs indexes
- file-based Data Lakes are very much designed around the partitions applied to the data, typically a minimum of some datetime series, and usually extending to other data attributes
- an absolute necessity that the data be broken up (partitioned) according to one or more attributes in that data table
- data of that size cannot be queried and accessed in a reasonable timeframe
- entire scans running on every single file of a few hundred TB data sources is not acceptable
- primary and secondary keys to be able to seek, join, and filter the datasets quickly
- normalised, leading to many smaller tables with one or two large fact tables
	- typically designed around the primary key, or uniqueness value of a dataset

### Walking the data model line between old and new
- with file based data models though, cannot support a large number of small lookup and dimension tables
	- big data tools will not respond well to such workloads
	- SQL relational data models> would be foolish not to normalise the data to the extreme

# Data Quality
- with the explosion of the size and the types of data stored in the cloud, data quality has become a real and formidable problem for anyone to tackle

### What is Data Quality
- "business" quality standards and the "data value" quality
- data quality is also extremely important from and end-user and business point of view
- poor data quality that users of our data notice first and immediately reduce their trust in data products
- good data quality: ensure that trust and long-term use of the data and pipelines engineers work on

### Business Quality
- rightly think about a column that should not be NULL
- simple constraints are core to data quality but are usually not the problems that are difficult to solve

### Human reasoning about data
- how we "reason" about the data as humans who consume the data
- expect pieces of information to be true about the data we use

### Double meanings
- identify and deal with all kinds of misunderstandings
- could be bad field names, data points that are too similar, or just ambiguity
-  struggle: no concrete quality definitions and rules surrounding the data
	- many people refer to the same data, but talking about different things or believe different things about that data

### Data value quality
- NOT NULL or NULL, or even value CONSTRAINTS x, y, or z
	- can contain any value
	- values are in a range
- as data grows in size and complexity it becomes a very serious and complex business to know what is happening over time to all those data points

### Measures of data quality
- correct header or column names
- correct file formatting
- correct data types
- value ranges and value integrity
- all fairly easy to approach and check with code in an automated fashion
- factors should be checked on each data set before its ingested
	- avoid costly pipeline downtime and bad data being propagated downstream causing trust and reliability issues 

### Correct header or column names
- unknown and unanticipated changes in column names
- most pipelines and data transformations that are even moderately complex rely on an expected setlist of column names from which the source data is pulled
- the minute column name changes typically means a pipeline or some processes shortly thereafter is going to break
- each time a new file or dataset hits out staging environment/server/cloud bucket, its farily simple to quickly open that file and pull the first line of the file (header)
- can automate alerts and quarantine or move the "bad" file or data into another area out of harm's way

### Correct data/file formatting
- format of the file or data being ingested
- wrong file extension showing up
- its very easy to write automated checks on file extensions to determine if we have received what our system is expecting
- a simple read of a dataset and grabbing the first line, after the header
	- we can easily and quickly check the format without reading the entire file

# DevOps for Data Engineers
### Dockerfiles and docker-compose
- dockerfiles level the playing fields by pre-packing all the OS system requirements and dependencies on a single easy-to-use source
- **why data need dockerfiles**
	- typical complex data pipelines and codebases require environment variables, configurations, specific directories, and code layout
- **dockerfile solve the complexity problem**
	- with a simple docker run or docker-compose up common, everything that is needed to run and test pipeline code is at your fingertips

### Reasons to use a Dockerfile for data pipelines
- no surprise updates and breakages due to OS or package updates
- easier onboarding new engineers into the codebase
- requirements, configuration, env vars all become easier to manage
- everyone is on the same page, no windows vs mac vs linux gotchas
- easier to transition code into a distributed environments (Kubernetes)
- better DevOps (code deployment) and unit-integration testing
- makes you better at the command line 

### Get started with dockerfiles
- install Docker desktop easy to use and easy to install
- understand DockerHub
- build Dockerfile, based on whatever OS you want, with whatever packages and tools you need, even layered on top of some Dockerfile form someone else

### docker-compose
- simply a way to have multiple services and images all work together and talk together
	- a great tool for more complex projects

### Dockerfile summary
- forces a more rigid development structure that is missing from a lot of data engineering code bases

### Unit testing
### increase learning
- when have no unit tests, usually the only other way to test changes on a pipelines to run it
	- sometimes easier said than done in a development environment
- **unit tests can be a great way to start learning a codebase, before simply just trying to read the whole codebase**

### Lead to better quality code
- anything is better than not breaking your code up into logical units that can be tested

### Reduce bugs
- DevOps: automating process that allows for the reduction of bugs make it into production
- automated unit tests are probably the number one way we can use DevOps to reduce the chances of bugs getting out
- reduces, or risk of making errors and protects developers from making human mistakes

### Deep dive pyspark unit testing
### setup directories and pytest

### Keys to writing good unit tests
- setting up docker to run our pyspark unit tests
	- dockerfile
	- docker-compose file

### CI/CD
- CI/CD is a major part of DevOps and has become critical to get good Data Engineering pipelines
- myriad of tools that will probably grow and expand
	- Jenkins, Gitlab/Hub, CI/CD runners

### Automation
