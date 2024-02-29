### Operating model

Following is a picture of the operating model for requesting and publishing PhPIDs. GSIDs can also be requested and published following the same processes. 

<img src="OperatingModel.png" alt="The PhPID operating model"/>
<br clear="all"/>

#### Operations
1. When a PhPID is needed for a product the medicinal product information is added to a request, submitted to the PhPID maintenance organisation.
2. The information in the request is validated and harmonized by a team of pharmacists, based on a set of business rules and the product SPC information.
3. The validated and harmonized data is entered as input to the generation of PhPIDs, levels 1 to 4.
4. A response to the request with the generated PhPIDs is sent. 
5. The newly generated PhPIDs are stored in the PhPID repository, where all generated PhPIDs are stored.

#### Corresponding FHIR operations 
1. A FHIR [Task](StructureDefinition-Task-who-php-phpid.html) is used to request a new PhPID where necessary information to complete the request is embedded in the contains section of the Task. See [PhPID request model](phpIdRequest.html) for detasils.  
2. While valitating the request the the status of the Task indicates to progress.  
3. The Task is _ready_ and transits to _completed_ via _in-progress_. 
4. The new (or already existing) PhPID is published in the output section of the Task and is thereafter publically available as an [AdministrativeProductDefinition](StructureDefinition-AdministrableProductDefinition-who-php.html) resource.
5. Searching for an existing PhPID can be done using standard search functionality. Available searhc and filter parameters is available in the Capability Statement.