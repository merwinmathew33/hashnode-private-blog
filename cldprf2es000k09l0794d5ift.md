# YAML -A Complete Guide from basic to Advance

YAML (Yet Another Markup Language) is a human-readable data serialization format used for storing and exchanging data. It is often used for configuration files, data exchange between languages and web development. YAML is designed to be easy to read and write, making it a popular choice for many applications. It supports data structures such as lists, associative arrays (dictionaries), and scalar types like strings and integers. Unlike XML or JSON, YAML uses indentation and simple punctuation to define the structure, making it less verbose and easier to read. YAML files typically have a .yaml or .yml extension.

## Use Cases

1. Configuration files: YAML is often used for configuration files due to its simplicity and ease of use.
    
2. Data exchange: YAML is often used for exchanging data between programming languages and platforms because of its versatility and compatibility with a wide range of systems.
    
3. Web development: YAML is used in web development for representing data structures such as frontend configurations, database models, and APIs.
    
4. Cloud computing: YAML is used in cloud computing platforms for defining infrastructure as code and configuration management.
    

## Basic Syntax

The basic syntax of YAML includes the following elements:

1. **Indentation**: In YAML, indentation is used to define the structure of the data. Each level of indentation represents a new nested structure.
    
2. **Comments**: YAML supports comments using the "#" symbol. Comments in YAML are ignored by the parser and are used to add notes or explanations to the code.
    
3. **Scalar Data Types**: YAML supports the following scalar data types:
    
    a. Strings: Strings in YAML can be defined using single or double quotes.
    
    * Folding strings: In YAML, you can fold a string into multiple lines by using the "&gt;" character. This tells the YAML parser to preserve the line breaks and treat the string as a single entity
        
    * Block strings:In YAML, block strings are represented as multi-line strings enclosed in triple quotes `"""` or with `|`
        
    
    b. Integers: Integers are whole numbers represented in YAML without quotes.
    
    c. Floats: Floating point numbers in YAML are represented with a decimal point.
    
    d. Boolean: YAML supports the values "true" and "false" for Boolean values.
    
4. **Lists**: Lists in YAML are represented as an ordered collection of scalar values, separated by dashes ("-").
    
5. **Associative Arrays (Dictionaries)**: Dictionaries in YAML are represented as key-value pairs separated by a colon (":").
    

Example:

```yaml
# This is a comment in YAML

# A string in YAML
name: "Merwin Mathew"

# An integer in YAML
age: 20

# A floating point number in YAML
weight: 55.5

# A Boolean value in YAML
is_member: true

# A list in YAML
fruits:
  - Apple
  - Orange
  - Banana

# A dictionary in YAML
address:
  street: "123 Main St"
  city: "Thrissur"
  state: "Kerala"
  country: "India"
```

As you can see in the example, YAML uses indentation, punctuation, and comments to define the structure of the data in a simple and readable format.

## Data Structures

YAML supports a variety of data structures, including:

1. Lists: Lists in YAML are used to represent an ordered collection of items, where each item is separated by a dash ("-"). For example:
    

```yaml
fruits:
  - Apple
  - Orange
  - Banana
```

1. Associative Arrays (Dictionaries): Associative arrays, also known as dictionaries or maps, are used to represent key-value pairs in YAML. The keys and values are separated by a colon (":"). For example:
    

```yaml
address:
  street: "123 Main St"
  city: "Thrissur"
  state: "Kerala"
  country: "India"
```

1. Nested Structures: YAML supports nested structures, allowing you to create complex data structures with nested lists, dictionaries, and scalar values. For example:
    

```yaml
person:
  name: "Merwin Mathew"
  age: 20
  address:
    street: "123 Main St"
    city: "Thrissur"
    state: "Kerala"
    country: "India"
```

In this example, the "person" dictionary contains a nested dictionary "address". This demonstrates how YAML can be used to represent complex data structures in a human-readable format.

## **Schemas & Tags**

A schema is a set of rules that describe how a YAML document should be structured, including what types of data are allowed and how the data should be organized. Schemas help ensure that a YAML document is well-formed and follows a certain format.

Tags are used to add additional information to YAML data, such as type information or metadata. A tag is a string that starts with an exclamation point (!) and is followed by a type indicator, such as "!!str" for a string or "!!map" for a mapping (associative array). Tags can be used to change the type of a value, specify custom data types, or define custom transformations.

Here is an example of using a tag to specify a custom data type in YAML:

```yaml
yamlCopy code# Define a custom date format
!date 2002-12-14
```

In this example, the `!date` tag is used to indicate that the string `2002-12-14` should be interpreted as a date.

## Advantages

YAML offers several advantages over other data serialization formats, such as XML and JSON:

1. Human-Readable: YAML is designed to be human-readable, making it easier to write and understand compared to XML or JSON.
    
2. Concise: YAML uses indentation to define data structures, which allows for a more concise and readable representation of data compared to XML or JSON.
    
3. Versatile: YAML supports a wide range of data structures, including scalar values, lists, dictionaries, and nested structures, making it a versatile data serialization format.
    
4. Easy to Use: YAML is easy to use and understand, making it a popular choice for configuration files, data exchange, and web development.
    
5. Good Support: YAML has good support across many programming languages and platforms, making it a popular choice for data exchange between systems.
    
6. Flexible: YAML is flexible and allows for optional syntaxes, such as quotes for strings, making it easy to customize the format to meet specific needs.
    

## Real-world examples of YAML

YAML is widely used in various domains and some real-world examples include:

1. ### **Configuration files:**
    
    YAML is often used to write configuration files, such as for applications, scripts, and systems. For example, a YAML configuration file for a web server might look like this:
    

```yaml
yamlCopy codeport: 8080
bind_address: 0.0.0.0
document_root: /var/www/html
```

This code is a YAML file that represents configuration settings for a web server. The file contains three key-value pairs.

1. port: "8080" is the port number the web server will listen on.
    
2. bind\_address: "0.0.0.0" is the IP address the web server will bind to. A value of "0.0.0.0" means the web server will listen on all available network interfaces.
    
3. document\_root: "/var/www/html" is the path to the root directory of the website the web server will serve. This is where the web server will look for HTML files and other assets to serve clients.
    
4. ### **Infrastructure as Code (IaC):**
    
    YAML is a popular data serialization format for Infrastructure as Code (IaC) tools, such as Ansible, Terraform, and Kubernetes. For example, a YAML file for a Kubernetes deployment might look like this:
    

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-web-app
  labels:
    app: my-web-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-web-app
  template:
    metadata:
      labels:
        app: my-web-app
    spec:
      containers:
      - name: my-web-app
        image: my-web-app:latest
        ports:
        - containerPort: 80
```

This code is a YAML file that defines a Kubernetes Deployment. The deployment is used to manage the deployment of a set of replicas of a web application.

1. apiVersion: The first line, "apiVersion", specifies the version of the Kubernetes API that this deployment is using. In this case, it's using the version "apps/v1".
    
2. kind: The second line, "kind", specifies the type of Kubernetes object being defined. In this case, it's a "Deployment".
    
3. metadata: The third line, "metadata", defines information about the deployment, such as its name and labels.
    

* name: "my-web-app" is the name of the deployment.
    
* labels: "app: my-web-app" is the label assigned to the deployment.
    

1. spec: The fourth line, "spec", defines the specification of the deployment, including the number of replicas, the selector, and the template used to create the replicas.
    

* replicas: "3" is the number of replicas of the web application that will be created.
    
* selector: "matchLabels: app: my-web-app" is used to select the pods that belong to this deployment. The deployment will only manage pods that have the label "app: my-web-app".
    
* template: defines the template used to create the replicas of the web application.
    
    * metadata: defines the labels for the replicas.
        
    * spec: defines the containers for the replicas.
        
        * name: "my-web-app" is the name of the container.
            
        * image: "my-web-app:latest" is the Docker image used to create the container.
            
        * ports: defines the ports that the container will listen on. In this case, the container will listen on port 80.
            

1. ### **Data Exchange:**
    
    YAML is commonly used to exchange data between systems, as it is a flexible and human-readable format. For example, a YAML file representing a customer order might look like this:
    

```yaml
customer_id: 12345
order_date: 2021-01-01
items:
  - item_id: 1
    name: "Apple"
    quantity: 2
    price: 0.99
  - item_id: 2
    name: "Orange"
    quantity: 3
    price: 0.79
```

This code is a YAML file that represents a customer's order. The order includes the customer's ID, the date of the order, and a list of items in the order.

1. customer\_id: "12345" is the ID of the customer who placed the order.
    
2. order\_date: "2021-01-01" is the date the order was placed.
    
3. items: The third line, "items", is a list of items in the order.
    

* item\_id: "1" is the ID of the first item in the order.
    
* name: "Apple" is the name of the first item in the order.
    
* quantity: "2" is the number of units of the first item in the order.
    
* price: "0.99" is the price of the first item in the order.
    

In conclusion, YAML is a versatile data serialization format that is widely used for a wide range of applications and is well suited for use cases that require human-readable data representations and simple data structures.

Thank you for visiting my blog! I hope you found the information you were looking for. If you have any questions or suggestions, please feel free to reach out to me. Don't forget to follow me on social media for updates and new content.

[twitter](https://twitter.com/merwin333)

[linkedin](https://www.linkedin.com/in/merwin-mathew/)