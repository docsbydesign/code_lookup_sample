# code_lookup_sample
This repo contains code examples that demonstrate the ICD-10 code lookup feature of the piClinic API.

This repo contains two examples that use the piClinic API:
* Making piClinic API calls from [Postman](https://www.getpostman.com/)
* Making piClinic API calls from within a Python application

See [piClinic API documentation](https://piclinic.org/api) for more information about the piClinic API.

After reviewing these examples, you should be familiar with the piClinic API and be able to access it from within your own Python program.

# Making piClinic API calls from Postman

Postman is an API development environment that lets you call a REST API through an interactive console.

The [postman](https://github.com/docsbydesign/code_lookup_sample/tree/master/postman) folder of this
repo contains a Postman collection of requests that demonstrate the
sequence of piClinic API calls that an application might use to access the _**icd**_ resource.

This sequence consists of:
1. Opening a session on the piClinic server and receiving an access token.
1. Calling a piClinic API several times.
1. Closing the session after access to the piClinic API is no longer needed.

## Download the repo

You can access the files for the examples from this site. You can also download the repo to access the files directly from your system by clicking the `Clone or download` button above or executing
this `git` command from the folder under which you want to install the files.

```
git clone git://github.com/docsbydesign/code_lookup_sample.git
```

## Making piClinic API calls using Postman

Opening the collection, requires [Postman](https://www.getpostman.com/) to be installed on your system.

Running the examples in the Postman collection can give you a sense of interacting with the API,
which can help you when you use the API in a program.

If you're new to Postman, review the documentation at [Getting started with Postman](https://learning.getpostman.com/getting-started/).

### Importing the Postman collection

A Postman collection is a set of API requests that can be made from Postman. This collection
demonstrates the piClinic API.

Open Postman and follow these steps to import the Postman collection:
1. Click the **Import** button.
2. Select the **Import from link** option.
3. Enter this URL, and then click **Import**.
```
https://raw.githubusercontent.com/docsbydesign/code_lookup_sample/master/postman/piClinicApiClass.postman_collection.json
```
4. Select the **Collections** tab to see the collection you just imported.

### Running the piClinic API requests in the collection

Open the collection in Postman to see these requests:
1. Open a piClinic session
2. Get a code description by ICD code lookup
3. Get a code description by ICD code lookup (en)
4. Get an ICD code by description search
5. Close the current piClinic session

Explore each of the sample requests in Postman by starting with the first one.
1. Open the `Open a piClinic session` request, and then open the request's **Body** tab.
1. Edit the username and password values and replace:
  * `REPLACE WITH YOUR USERNAME` with the username you were provided.
  * `REPLACE WITH YOUR PASSWORD` with the password you were provided.
1. Click **Save**, and then click **Send**.
1. Review the response **Body** to see the data returned in the response.

For each of the other requests listed above:
1. Open the request and click **Send**.
2. Review the parameters and the response to get to know the API.

**Remember** that the piClinic API requires a valid session token to access most of its resources so the `Open a piClinic session` request must be sent first to obtain a valid session token for the other requests.

## Making piClinic API calls from within a Python application

The [exercises](https://github.com/docsbydesign/code_lookup_sample/tree/master/exercises) folder
contains these Python scripts to demonstrate how to access the piClinic API from within an application.
Use your favorite Python development environment to review and run them in this sequence.
If you don't have a favorite, you can view them in a text editor and run them from a terminal or console window.

1. piclinic_session.py
1. piclinic_lookup_code.py
1. piclinic_lookup_code_en.py
1. piclinic_search_code_en.py

NOTE that these samples run on Python 3 and import the `requests` module.
If you don't have the `requests` module installed on your system, you can
install it by running the following command line on your Mac:

```
python3 -m pip install requests
```
or from your PC:
```
python -m pip install requests
```

### credentials


### piclinic_session.py

Opens and closes a piClinic session.

The methods in this script show how to access the **session** resource to
obtain an access token and close the session when finished. These methods
will be imported by the other scripts to perform those functions.

This script makes API calls similar to the `Open a piClinic session` and `Close the current piClinic session` requests in the Postman collection.

### piclinic_lookup_code.py

Opens a piClinic session to look up an ICD-10 code and then closes the session.

This script imports the session methods from `piclinic_session.py` and then
calls the **icd** resource to look up an ICD-10 code and get its description.

This script makes an API call similar to the `Get a code description by ICD code lookup` request in the Postman collection.

Try changing the code value to look up the description of another ICD-10 codes. For example, try looking up the description for ICD-10 code: `J00`.

### piclinic_lookup_code_en.py

Opens a piClinic session to look up an ICD-10 code in English and then closes the session.

This script imports the session methods from `piclinic_session.py` and then
calls the **icd** resource to look up an ICD-10 code and get its description in English.

This script makes an API call similar to the `Get a code description by ICD code lookup (en)` request in the Postman collection.

Try changing the code value to look up the description of another ICD-10 codes as you did in the previous example.

### piclinic_search_code_en.py

Opens a piClinic session to search for the ICD-10 codes that contain a specific text in English and then closes the session.

This script imports the session methods from `piclinic_session.py` and then
calls the **icd** resource to search for the ICD-10 codes based on their description in English.

This script makes an API call similar to the `Get an ICD code by description search` request in the Postman collection.

Try changing the search text to look up some other ICD-10 codes.
