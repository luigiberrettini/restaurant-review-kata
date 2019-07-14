# Restaurant review kata


Company X, founded 12 years ago, owns a restaurant review site/app which had a quick and massive
customer adoption.

The rapid pace, at which the business grew, caused the architecture of the system to evolve in a very ad-hoc and organic way.

### Current architecture
 - Front office single page application written in React
 - Back office single page application written in React used by the Customer Success team
 - REST API implemented as a PHP 5 application containing all the business logic
 - MySQL database containing all data

### Business capabilities
 1. Home page with the latest published reviews and featuring up to 3 restaurants near the user location
 2. Restaurant profile page with:
     - promotion text, relevant information and photos by the restaurant owner
     - reviews and photos by the users
 3. User admin page for users to administer their reviews and account details
 4. Customer admin page for restaurant owners to manage their account and edit the content for their restaurant profile
 5. Search page
 6. User reviews moderation before publication (back office app)
 7. Paid subscription management and initial restaurant profile setup (back office app)

### Main issues
 1. Using a single application for the REST API has a negative impact on agility (longer development cycles) and scalability (cost inefficient)
 2. It is not possible to pay subscriptions online: new accounts are set up by the Customer Success once the confirmation of the payment is received
 3. Users have to scroll through all the restaurant reviews to understand what are the
positive and negative points about a restaurant and this can take a long time and be a bit
confusing, especially when a quick decision is needed


## Goal
Design the evolution of the current system to:
 - provide a payment system to allow subscription to be paid online via Visa or PayPal automating account setup on payment
 - provide a real-time review summary, on the restaurant profile page, containing:
    - the top 2 positive topics that people are mentioning in reviews
    - the top 2 negative (if any) topics that people are mentioning in reviews
    - how does the restaurant compare with the 2 closest restaurants


## Requirements
 - Make it easier to scale the number of teams simultaneously working on the product
 - Allow horizontal scaling in order to keep up with the increasing number of users
 - Design for resiliency and reliability (fault tolerance and disaster recovery), handling both unexpected and expected (on specific days and times) traffic spikes, while keeping running costs as low as possible
 - Keep page load times under 2 seconds
 - Describe how to adopt the new architecture to allow the business to keep evolving i.e. to keep releasing new features during the migration
 - Describe how to enable the development lifecycle to:
   - be as automated and optimized as possible
   - allow for quick time to market (from code to production)
   - allow for high reliability when releasing new features (including quick roll-back/roll-forward)
   - allow for gradual feature releases (by percentage of traffic of location)
 - Detail the tools to be used for centralized logging and real time monitoring
 - Detail assumptions and justify your choices


## Team structure
The engineering department is split across two different countries and it is composed by:
 - 3 features teams (1 Team Lead + 2 front-end devs + 2 back-end devs + 1 QA engineer)
 - 1 DevOps team (1 Team Lead + 4 DevOps engineers)

There are plans to increase the number of feature teams, as much as the new architecture will allow.

Software developers are highly proficient in PHP (Symfony) and Javascript (React and Node.js) but are willing and able to learn new technologies and programming languages.