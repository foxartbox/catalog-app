FORMAT: 1A
HOST: http://52.69.214.151/

# Papers

# Error Types

+ Response 400 (application/json)

    + Body

            {
                "message": 
                    [
                        "fieldname": 
                        [
                            "Some error"
                        ]
                    ]
            }
            
+ Response 405 (application/json)

    + Body

            {
                "message": "Some error"
            }  

# Group Account

## /signup

### Create a New User [POST]

+ Parameters
    + username (required, string, `user@exmple.com`) ... Email as username
    + password (required, string, `asdQWE123`) ... Password
    + fullname (required, string, `John Snow`) ... Fullname

+ Request  (application/json)

    + Body

            {
                "username": "user@exmple.com",
                "password": "SomeStrongPassword"
            }

+ Response 201 (application/json)

    Success response

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68"
            }

## /signin

+ Parameters
    + username (required, string, `user@exmple.com`) ... Email as username
    + password (required, string, `asdQWE123`) ... Password

### Login with exist user [POST]

+ Request  (application/json)

    + Body
    
            {
                "username": "user@example.com",
                "password": "asdQWE123"
            }

+ Response 200 (application/json)

    Success response

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68"
            }
            
## /signout

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token

### Logout [POST]

+ Request  (application/json)

    + Body
    
            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68"
            }

+ Response 200

## /account

### Receive a Account Data [GET]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token

+ Response 200 (application/json)

    Success response

        {
            "User": 
            {
                "username": "user@example.com",
                "fullname": "John Snow"
            },
            "Organization": 
            {
                "id": 123,
                "title": "Capsule Corporation"
            }
        }
        
### Update a Account Data [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + user.username (optional, string, `user@exmple.com`) ... Email as username
    + user.fullname (optional, string, `John Snow`) ... Fullname

+ Request  (application/json)

    + Body
    
            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "user":  {
                    "username": "user@exmple.com",
                    "fullname": "John Snow"
                }
            }

+ Response 200

# Group Organizations

## /organizations

### List of Projects [GET]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token

+ Response 200 (application/json)

    Success response

    + Body
    
            {
                "organizations": [
                    {
                        "Organization": 
                            {
                                "id": 1,
                                "title": "Project name",
                                "order_index": 1
                            }
                    },
                    {
                        "Organization": 
                            {
                                "id": 1,
                                "title": "Project name",
                                "order_index": 1
                            }
                    }
                ]
            }

## /organizations/organization

### Create a New Organization [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + organization.type (required, int, `1`) ... 1 - Company, 2 - Self-employment
    + organization.title (optional, string, `Some company`) ... Title of company (required for company)
    + organization.first_name (optional, string, `John`) ... First name of self-employer (required for self-employer)
    + organization.last_name (optional, string, `Smith`) ... Last name of self-employer (required for self-employer)
    + organization.address.postcode (optional, string, `1100004`) ... Post code
    + organization.address.country (optional, string, `Japan`) ... Country
    + organization.address.state (optional, string, `Tokyo`) ... State
    + organization.address.city (optional, string, `Taito-ku`) ... City
    + organization.address.street (optional, string, `Shitaya 1-13-7`) ... Street
    + organization.email (optional, string, `example@example.com`) ... Email
    + organization.phonenumber (optional, string, `+81-80-4737-6575`) ... Phonenumber

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "organization": 
                {
                    "type": 1,
                    "title": "Some company",
                    "address": 
                    {
                        "postcode": "1100004",
                        "country": "Japan",
                        "state": "Tokyo",
                        "city": "Taito-ku",
                        "street": "Shitaya 1-13-7",
                    },
                    "email": "example@example.com",
                    "phonenumber": "+81-80-4737-6575"
                }
            }

+ Response 200 (application/json)

    + Body
    
            {
                "organization_id": 123
            }
           
### Update a Organization [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + organization.id (required, int, `1`) ... Organization ID
    + organization.type (required, int, `1`) ... 1 - Company, 2 - Self-employment
    + organization.title (optional, string, `Some company`) ... Title of company (required for company)
    + organization.first_name (optional, string, `John`) ... First name of self-employer (required for self-employer)
    + organization.last_name (optional, string, `Smith`) ... Last name of self-employer (required for self-employer)
    + organization.address.postcode (optional, string, `1100004`) ... Post code
    + organization.address.country (optional, string, `Japan`) ... Country
    + organization.address.state (optional, string, `Tokyo`) ... State
    + organization.address.city (optional, string, `Taito-ku`) ... City
    + organization.address.street (optional, string, `Shitaya 1-13-7`) ... Street
    + organization.email (optional, string, `example@example.com`) ... Email
    + organization.phonenumber (optional, string, `+81-80-4737-6575`) ... Phonenumber

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "organization": 
                {
                    "id": 1,
                    "type": 1,
                    "title": "Some company",
                    "address": 
                    {
                        "postcode": "1100004",
                        "country": "Japan",
                        "state": "Tokyo",
                        "city": "Taito-ku",
                        "street": "Shitaya 1-13-7",
                    },
                    "email": "example@example.com",
                    "phonenumber": "+81-80-4737-6575"
                }
            }

+ Response 200 (application/json)

### Receive a Organization Data [GET]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + organization_id (required, string, `123`) ... Organization ID

+ Response 200 (application/json)

    + Body

            {
                "organization": 
                {
                    "id": 1,
                    "type": 1,
                    "title": "Some company",
                    "address": 
                    {
                        "postcode": "1100004",
                        "country": "Japan",
                        "state": "Tokyo",
                        "city": "Taito-ku",
                        "street": "Shitaya 1-13-7",
                    },
                    "email": "example@example.com",
                    "phonenumber": "+81-80-4737-6575"
                }
            }

# Group Projects

## /projects/projects

### List of Projects [GET]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + organization_id (required, int, `1`) ... Organization ID
    + search_keywords (optional, string, `Some Project LLC`) ... Keywords string
    + paging_size (optional, integer, `20`) ... Count of items in response
    + paging_offset (optional, integer, `10`) ... Offset in items for paging

+ Response 200 (application/json)

    Success response

    + Body
    
            {
                "projects": [
                    {
                        "Project": 
                            {
                                "id": 1,
                                "title": "Project name",
                                "updated_at": "2015-01-01 01:01:01",
                            }
                    },
                    {
                        "Project": 
                            {
                                "id": 2,
                                "title": "Project name",
                                "updated_at": "2015-01-01 01:01:01",
                            }
                    }
                ],
                "total_items_count": 123
            }

## /projects/project

### Create a New Project [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + organization.id (required, int, `123`) ... Organization ID
    + project.title (required, string, `Some project`) ... Title of project
    + project.description (optional, string, `Some description`) ... Description of project

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "organization": 
                {
                    "id": 123
                }
                "project": 
                {
                    "title": "Some project",
                    "description": "Some description"
                }
            }

+ Response 200 (application/json)

    Success response

    + Body
    
            {
                "project_id": 123
            }
           
### Update a Project [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project.id (required, string, `123`) ... Id of project
    + project.title (optional, string, `Some project`) ... Title of project
    + project.description (optional, string, `Some description`) ... Description of project
    + project.nda_document_usage (optional, boolean, `1`) ... Usage for NDA document
    + project.contract_document_usage (optional, boolean, `1`) ... Usage for Contract document
    + project.technical_description_document_usage (optional, boolean, `1`) ... Usage for Technical Description document
    + project.quotation_document_usage (optional, boolean, `0`) ... Usage for Quotation document
    + project.project_calendar_document_usage (optional, boolean, `1`) ... Usage for Product Calender document
    + project.payment_calendar_document_usage (optional, boolean, `1`) ... Usage for Payment Calender document
    
+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "project": 
                {
                    "id": "123"
                    "title": "Some project",
                    "description": "Some description",
                    "nda_document_usage": 1,
                    "contract_document_usage": 1,
                    "technical_description_document_usage": 1,
                    "quotation_document_usage": 0,
                    "project_calendar_document_usage": 1,
                    "payment_calendar_document_usage": 1
                }
            }
            
+ Response 200

### Receive a Project Data [GET]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project_id (required, string, `123`) ... Id of project

+ Response 200 (application/json)

    + Body

            {
                "project": 
                {
                    "id": "123"
                    "title": "Some project",
                    "description": "Some description",
                    "nda_document_usage": 1,
                    "contract_document_usage": 1,
                    "technical_description_document_usage": 1,
                    "quotation_document_usage": 0,
                    "project_calendar_document_usage": 1,
                    "payment_calendar_document_usage": 1
                }
            }
            
# Group Project Calendar

## /ProjectCalendar

### Create/Update Section of Project Calendar [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project.id (required, string, `123`) ... Id of project
    + project.project_calendar.sections.N.id (optional, int, `123`) ... Section ID
    + project.project_calendar.sections.N.title (required, string, `Test Section`) ... Section title
    + project.project_calendar.sections.N.order_index (required, int, `1`) ... Section order index

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "project": 
                {
                    "id": 123,
                    "project_calendar": 
                    {
                        "sections": 
                        [
                            {
                                "title": "Test Section",
                                "order_index": 1,
                            }
                        ]
                    }
                }
            }
            
+ Response 200

### Create/Update Item of Project Calendar Section [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project.id (required, string, `123`) ... Id of project
    + project.project_calendar.sections.N.id (required, int, `123`) ... Section ID
    + project.project_calendar.sections.N.items.N.id (optional, int, `123`) ... Item ID
    + project.project_calendar.sections.N.items.N.order_index (required, int, `1`) ... Item Order Index
    + project.project_calendar.sections.N.items.N.text (required, string, `Test test`) ... Item Text
    + project.project_calendar.sections.N.items.N.start_date (required, date`2015-12-31`) ... Start Date
    + project.project_calendar.sections.N.items.N.end_date (required, date, `2015-12-31`) ... End Date

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "project": 
                {
                    "id": 123,
                    "project_calendar": 
                    {
                        "sections": 
                        [
                            {
                                "title": "Test Section",
                                "order_index": 1,
                                "items":
                                [
                                    {
                                        "id": 1,
                                        "text": "Test",
                                        "start_date": "2015-12-31",
                                        "end_date": "2016-01-30"
                                    }
                                ]
                            }
                        ]
                    }
                }
            }
            
+ Response 200

### Delete Section of Project Calendar [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project.id (required, string, `123`) ... Id of project
    + project.project_calendar.sections.N.id (required, int, `123`) ... Section ID
    + project.project_calendar.sections.N.delete (required, int, `1`) ... Delete section flag

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "project": 
                {
                    "id": 123,
                    "project_calendar": 
                    {
                        "sections": 
                        [
                            {
                                "id": 123,
                                "delete": 1,
                            }
                        ]
                    }
                }
            }
            
+ Response 200

### Delete Item of Project Calendar Section [POST]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project.id (required, string, `123`) ... Id of project
    + project.project_calendar.sections.N.id (required, int, `123`) ... Section ID
    + project.project_calendar.sections.N.items.N.id (required, int, `123`) ... Item ID
    + project.project_calendar.sections.N.items.N.delete (required, int, `1`) ... Delete item flag

+ Request  (application/json)

    + Body

            {
                "session": "485fc381-e790-47a3-9794-1337c0a8fe68",
                "project": 
                {
                    "id": 123,
                    "project_calendar": 
                    {
                        "sections": 
                        [
                            {
                                "id": 123,
                                "delete": 1,
                            }
                        ]
                    }
                }
            }
            
+ Response 200


### Receive a Project Calendar [GET]

+ Parameters
    + session (required, string, `485fc381-e790-47a3-9794-1337c0a8fe68`) ... Session token
    + project_id (required, string, `123`) ... Id of project

+ Response 200 (application/json)

    + Body

            {
                "project_calendar": 
                {
                    "id": 123,
                    "sections": 
                    [
                        {
                            "id": 123,
                            "title": "Test Section",
                            "order_index": 1,
                            "items": 
                            [
                                "id": 123,
                                "text": "Test Item",
                                "start_date": "2015-12-31",
                                "end_date": "2016-12-31",
                                "order_index": 1
                            ]
                        }
                    ]
                }
            }            