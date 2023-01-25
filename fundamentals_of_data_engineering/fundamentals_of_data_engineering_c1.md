# Fundamentals of Data Engineering
# Data Engineering Described
## Data Engineering Defined
- development, implementation, and maintenance of systems and processes that take in raw data and produce high-quality, consistent information that supports downstream use cases, such as analysis and machine learning
- intersection of security, data management, DataOps, data architecture, orchestration, and software engineering
- manages the data engineering lifecycle, beginning with getting data from source systems and ending with serving data for use cases, such as analysis or machine learning

## Data Engineering Lifecycle
- gives the data engineers the holistic context to view their role
- stages of data engineering lifecycle:
	- generation
	- storage
	- ingestion
	- transformation
	- serving
- notion of undercurrents > critical ideas across the entire lifecycle
	- security, data management, DataOps, data architecture, orchestration, software engineering

## Data Engineering and Data Science
- data engineering sits upstream from data science
- provide the inputs used by data scientists (downstream from data engineering) who convert these inputs into something useful
- **data science hierarchy of needs**
	- collect > move/store > explore/transformation > aggregate/label > learn optimize
- data scientists aren't typically trained to engineer production-grade data systems
	- end up doing work haphazardly
	- lack support and resources of a data engineer

## Data Engineering skills and activities
- requires an understanding of how to evaluate data tools and how they fit together across the data engineering lifecycle
- balancing act of data engineering
	- cost - agility - scalability - simplicity - reuse - interoperability

## Data Maturity and the Data Engineer
- data maturity: the progression toward higher data utilization, capabilities, integration across the organization
- data maturity model
	- starting with data
	- scaling with data
	- leading with data
- company may have fuzzy, loosely defined goals or no goals
	- data architecture and infrastructure are in the very early stages of planning and development  
	- headcount in the single digits
- **starting with data**: should focus on the following in organizations getting started with data:
	- get buy in from key stake holders, including executive management
		- should have a sponsor for critical initiatives to design and build a data architecture to support the company goals
	- define the right data architecture
		- determining the business goals and the competitive advantage you're aiming to achieve with data initiative
	- identify and audit data that will support key initiatives and operate within the data architecture you designed
	- build a solid data foundation for future data analyst and data scientists to generate reports and models that provide competitive value
- **scaling with data**
	- establish formal data practices
	- create stable and robust data architecture
	- adopt DevOps and DataOps practices
	- build systems that support ML
	- continue to avoid undifferentiated heavy lifting and customize only when a competitive advantage results
- **leading with data**
	- create automation for the seamless introduction and usage of new data
	- focus on building custom tools and systems the leverage data as a competitive advantage
	- focus on the "enterprise" aspects of data > data management (+data governance & quality)
		- DataOps
	- expose and disseminate data throughout the organization
		- data catalogs, data lineage tools, metadata management systems
	- collaborate efficiently with software engineers, ML engineers, analysts
	- create a community where people can collaborate

## Background and skills of a Data Engineer
### Business Responsibilities
- know how to communicate with non-technical and technical people
- understand how to scope and gather business and product requirements
- understand cultural foundations of Agile, DevOps, DataOps
- control costs
- learn continuously

### Technical Responsibilities
- focus on high level abstraction or writing pipelines as code with an orchestration framework
- languages:
	- SQL
	- Python
	- JVM Languages (Java, Scala)
	- bash

### Type A Data Engineers
- abstraction
- manage the data engineering lifecycle mainly by using entirely off the shelf products

### Type B Data Engineers
- build
- build data tools and systems that scale and leverage a company's core competency and competitive advantage

## Internal Facing vs. External Facing Data Engineers
- external facing data engineers typically aligns with the users of external facing applications
	- builds and manages the systems that collect, store, process transactional and event data from these applications
	- larger concurrency workloads
- internal facing data engineer focuses on activities crucial to the needs of the business and internal stakeholders

## Data Engineers and other technical roles
- data architects: design the blueprint  for organizational data management, mapping out processes and overall data architecture and systems
	- implement policies for managing data across silos and business units
	- steer global strategies such as data management and data governance
- software engineers: build software and systems that run a business
	- largely responsible for the internal data that data engineers will consume and process
-  devops engineers and site-reliability engineers: produce data through operational monitoring
- data scientists: build forward looking models to make predictions and recommendations
- data analysts: seek to understand the business performance and trends
- machine learning engineers and  AI researchers
	- ML Engineers develop advanced ML techniques, train models, design and maintain the infrastructure running ML processes in a scaled production environment 
	- AI Researches work on new, advanced ML techniques

## Data Engineers and Business Leadership
- data in the C-suite
	- increasingly involved in data and analytics
	- concern with the initiatives that were once the exclusive province of IT
- **Chief Executive Officer**
	- define a vision in collaboration with technical c-suite roles and company data leadership
	- data engineers and managers maintain a map of what data is available to the organization (internally and externally)
		- study primary data architectural changes in collaboration with other engineering roles
- ** Chief Information Officer**
	- senior c-suite executive responsible for information technology in an organization
	- must possess deep knowledge of information technology and business processes
	- direct the IT organization, setting ongoing policies
	- often collaborate with data engineers and architects to map out major initiatives and make strategic decisions on adopting major architectural elements
- **Chief Technology Officer**
	- similar to CIO but faces  outward
	- owns the key technological strategy and architectures for external facing applications 
- **Chief Data Officer**
	- responsible for a company's data assets and strategy
	- focused on data's business utility 
		- should also have a strong technical grounding
	- oversee data products, strategy, initiatives, core functions (master data management, data privacy)
- **Chief Analytics Officer**
	- responsible for analytics, strategy, decision making for the business
	- may oversee data science and ML
- **Chief Algorithms Officer**
	- focused specifically on data science and M:
	- expected to be conversant in current ML research and have deep technical knowledge for the company's ML initiatives

### Data Engineers and Project Managers
- large initiatives often benefit from project management
- project managers direct traffic and serve as gatekeepers
- filter a long list of requests and prioritize critical deliverables to keep projects on track and better serve the company

### Data Engineers and Product Managers
- oversee product development (often owning product lines)
- balance the activity of technology teams against the needs of the customers and business

