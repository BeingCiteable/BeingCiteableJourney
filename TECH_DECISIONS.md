# Technology Decisions Log

_Documenting all major tech choices and reasoning for the Being Citeable project_

## Week 1 Decisions (June 30 - July 6, 2025)

### Decision #1: Cloud Platform Choice

**Status:** ✅ Decided
**Options:** Azure vs AWS vs Google Cloud vs Supabase + Vercel
**Choice:** Azure
**Date:** July 1, 2025
**Reasoning:** The team has extensive experience with the Microsoft stack. This makes Azure the natural choice for leveraging existing knowledge and ensuring seamless integration with the development tools and frameworks the team is most comfortable with.

#### Azure
**Pros:**
- Excellent integration with Microsoft ecosystem (if using .NET/C#)
- Strong enterprise support and compliance certifications
- Competitive pricing for compute and storage
- Good AI/ML services integration
- Familiar for teams already using Microsoft tools

**Cons:**
- Steeper learning curve for non-Microsoft developers
- Less mature than AWS in some service areas
- Documentation can be inconsistent
- Fewer third-party integrations compared to AWS

#### AWS
**Pros:**
- Most mature and feature-rich cloud platform
- Largest ecosystem of third-party tools and integrations
- Excellent documentation and community support
- Best-in-class reliability and performance
- Widest range of services and regions

**Cons:**
- Can be expensive, especially with poor resource management
- Complex pricing structure
- Overwhelming number of options can lead to analysis paralysis
- Vendor lock-in concerns

#### Google Cloud
**Pros:**
- Excellent for data analytics and machine learning
- Competitive pricing, especially for compute
- Strong Kubernetes support (they created it)
- Good for teams already using Google Workspace
- Innovative networking and security features

**Cons:**
- Smaller ecosystem compared to AWS/Azure
- Less enterprise adoption
- Some services are less mature
- Fewer compliance certifications than competitors

#### Supabase + Vercel
**Pros:**
- Developer-friendly with excellent DX
- Fast deployment and scaling
- Built-in auth, database, and real-time features
- Great for MVP and rapid prototyping
- Generous free tiers
- Modern tech stack (PostgreSQL, PostgREST)

**Cons:**
- Less control over infrastructure
- Potential vendor lock-in to Supabase ecosystem
- May hit scaling limitations for very large applications
- Fewer enterprise features and compliance options
- Relatively new platform with smaller community

---

### Decision #2: Authentication Strategy

**Status:** ✅ Decided
**Options:** Microsoft Entra External ID vs Custom Auth vs Auth0 vs Supabase
**Choice:** Microsoft Entra External ID
**Date:** July 2, 2025
**Reasoning:** Costs nothing in the beginning and is easy to build into the applications. Given the team's familiarity with the Microsoft stack and the choice of Azure as the cloud platform, Entra External ID provides seamless integration and a cost-effective solution for authentication.

#### Microsoft Entra External ID
**Pros:**
- Seamless integration with Microsoft ecosystem
- Enterprise-grade security and compliance
- Built-in multi-factor authentication
- Good for B2B scenarios with existing Microsoft customers
- Extensive identity management features

**Cons:**
- Complex setup and configuration
- Expensive for high-volume consumer applications
- Primarily optimized for Microsoft stack
- May be overkill for simple authentication needs
- Learning curve for non-Microsoft developers

#### Custom Auth
**Pros:**
- Full control over authentication flow and data
- No vendor lock-in
- Can be optimized for specific use cases
- No recurring subscription costs
- Complete customization of user experience

**Cons:**
- Significant development time and complexity
- Security risks if not implemented correctly
- Ongoing maintenance and updates required
- Need to handle compliance requirements manually
- Higher likelihood of bugs and vulnerabilities

#### Auth0
**Pros:**
- Industry-leading authentication platform
- Extensive integrations and social login options
- Strong security features and compliance
- Excellent developer experience and documentation
- Handles complex authentication scenarios well

**Cons:**
- Can be expensive as user base grows
- Vendor lock-in concerns
- May be overly complex for simple use cases
- Pricing model can be unpredictable
- Additional service dependency

#### Supabase Auth
**Pros:**
- Integrated with Supabase ecosystem
- Simple setup and configuration
- Built-in support for social logins
- Row Level Security (RLS) integration
- Good for rapid development and prototyping

**Cons:**
- Less mature than dedicated auth providers
- Fewer advanced enterprise features
- Tied to Supabase platform
- Limited customization options
- Smaller community and fewer resources

---

### Decision #3: Database Choice

**Status:** ✅ Decided
**Options:** Azure SQL for PostgreSQL vs Azure SQL (MSSQL serverless) vs CosmosDB vs PostgreSQL vs Supabase
**Choice:** Azure SQL (MSSQL Serverless) with auto pause
**Date:** July 2, 2025
**Reasoning:** Familiarity with the technology means speed over cost. The team can leverage existing SQL Server knowledge for faster development, while optimizing costs by using the auto pause feature to minimize expenses during low-usage periods.

#### Azure SQL for PostgreSQL
**Pros:**
- Managed PostgreSQL service with Azure integration
- Automatic backups and high availability
- Good performance and scalability options
- PostgreSQL's excellent JSON/JSONB support
- Strong ACID compliance and relational features

**Cons:**
- Higher cost than self-managed PostgreSQL
- Tied to Azure ecosystem
- May have limitations compared to self-hosted PostgreSQL
- Less control over server configuration
- Potential vendor lock-in

#### Azure SQL (MSSQL Serverless)
**Pros:**
- Serverless model with automatic scaling
- Pay-per-use pricing model
- Excellent integration with Microsoft stack
- Enterprise-grade features and security
- Familiar for teams with SQL Server experience

**Cons:**
- Cold start latency issues
- More expensive for consistent workloads
- Limited to Microsoft ecosystem
- Less flexibility compared to other database options
- Vendor lock-in concerns

#### CosmosDB
**Pros:**
- Global distribution and multi-region replication
- Multiple API support (SQL, MongoDB, Cassandra, etc.)
- Automatic scaling and partitioning
- Low latency worldwide
- Serverless and provisioned throughput options

**Cons:**
- Complex pricing model that can become expensive
- Learning curve for query optimization
- Limited complex query capabilities
- Vendor lock-in to Azure
- Overkill for simple relational data needs

#### PostgreSQL (Self-hosted/Other providers)
**Pros:**
- Open source with no licensing costs
- Excellent performance and feature set
- Strong community and ecosystem
- Full control over configuration and optimization
- Can be hosted anywhere (AWS RDS, Google Cloud SQL, etc.)

**Cons:**
- Requires more operational overhead
- Need to handle backups, monitoring, and maintenance
- Scaling requires more planning and effort
- Security and compliance management responsibility
- Infrastructure management complexity

#### Supabase Database
**Pros:**
- Managed PostgreSQL with built-in real-time features
- Integrated with Supabase ecosystem (auth, storage, edge functions)
- Excellent developer experience with auto-generated APIs
- Built-in Row Level Security (RLS)
- Generous free tier for development and small projects
- Real-time subscriptions out of the box
- Automatic backups and point-in-time recovery

**Cons:**
- Vendor lock-in to Supabase platform
- Less control over database configuration than self-hosted
- Newer platform with smaller enterprise adoption
- Limited geographic regions compared to major cloud providers
- May hit scaling limitations for very large datasets
- Pricing can become expensive at scale
- Fewer advanced PostgreSQL extensions available

---

### Decision #4: CI/CD Platform Choice

**Status:** ✅ Decided
**Options:** GitHub Actions vs Azure DevOps vs Atlassian (Bitbucket Pipelines)
**Choice:** GitHub Actions
**Date:** June 30, 2025
**Reasoning:** GitHub Actions is natively integrated with the source code hosting and provides very comprehensive features. This eliminates the need for additional integrations and offers a streamlined development experience with the repository and CI/CD pipeline in the same platform.

#### GitHub Actions
**Pros:**
- Seamless integration with GitHub repositories
- Extensive marketplace of pre-built actions
- Free for public repositories and generous free tier for private
- YAML-based configuration that's easy to version control
- Strong community support and documentation
- Built-in secrets management
- Matrix builds for testing across multiple environments

**Cons:**
- Can become expensive for heavy usage on private repositories
- Limited advanced enterprise features compared to dedicated CI/CD tools
- Vendor lock-in to GitHub ecosystem
- Less sophisticated deployment pipeline management
- Limited built-in reporting and analytics

#### Azure DevOps
**Pros:**
- Excellent integration with Microsoft ecosystem and Azure
- Comprehensive ALM (Application Lifecycle Management) suite
- Advanced work item tracking and project management
- Robust release management and deployment pipelines
- Strong enterprise features and compliance
- Good integration with on-premises and hybrid environments
- Extensive reporting and analytics capabilities

**Cons:**
- Can be complex and overwhelming for simple projects
- Steeper learning curve compared to other options
- More expensive for large teams
- UI can feel dated compared to modern alternatives
- Requires more setup and configuration

#### Atlassian Bitbucket Pipelines
**Pros:**
- Tight integration with Atlassian suite (Jira, Confluence)
- Docker-native approach to build environments
- Good for teams already using Atlassian tools
- Competitive pricing model
- Built-in deployment capabilities
- Easy YAML configuration

**Cons:**
- Smaller ecosystem compared to GitHub Actions or Azure DevOps
- Less mature than other CI/CD platforms
- Limited free tier (only 50 build minutes per month)
- Fewer integrations with third-party tools
- Less community support and fewer resources
- Performance can be slower than competitors

---

## Additional Notes

**Environment Strategy:** For cost-saving reasons, there will be no staging/test environment in the beginning. The project will operate with only development and production environments until close to launch, when a staging environment may be introduced for final testing and validation.

---

_More decisions will be logged as we make them throughout the week..._
