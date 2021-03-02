---
layout: post
title: REST API using Spring
date: 2021-02-17
github_link: https://github.com/pranjalsrajput/REST-API-using-Spring
description: REST API using Spring
img: projects/rest.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [REST, Webservice]
permalink: "/restapi-project/"
---

# REST API using Spring

A REST API is developed using spring framework. The API takes the input, and provides the results of task 1 and task 2. The two tasks are described below in details.

# Tasks 

## Task 1 - The Algorithm

Suppose we have some input data describing relationships between nodes over multiple generations. The input data is formatted as a list of 
(parent, child) pairs, where each is assigned a unique integer 
identifier.

For example, in this diagram, 3 is a child of 10 and 2, and 5 is a child of 4:

```            
10  2   4
 \ /   / \
  3   5   8
   \ / \   \
    6   7   9
```
Sample graph as input data

```java
// Java 
int[][] parentChildPairs = new int[][] {
    {10, 3}, {2, 3}, {3, 6}, {5, 6}, {5, 7},
    {4, 5}, {4, 8}, {8, 9}
}
```

The main task is to take this data as input and return collections:

* one containing all individuals with zero known parents, and 
* one containing all individuals with exactly one known parent.

Sample result for the sample graph

```
Zero parents: 10, 2, 4
One parent: 5, 7, 8, 9
```


###  Requirements

* Output order is irrelevant.
* The IDs are not guaranteed to be contiguous.
* The input is not necessarily a connected graph. There may be >3 generations.
* No node in the input set will have more than two parents, nor will there be duplicate entries.
* No node in the input is their parent.


## Task 2 - Complex relationships

Based on Task 1, check that if any two given individuals in the dataset share at least one known ancestor.


Example based on the sample graph of Task 1 two nodes input:
```
[3, 8] => false
[5, 8] => true
[6, 8] => true
```

## Task 3 - REST with Spring

The task is to develop a REST service that provides Task 1 and Task 2 via an API. Given an input graph, the application must provide the result for Task 1 and Task 2 via API. For Task 2 it shall take user input (for the node pair).

## Working of Task 01

Given a graph as input, the task is to find nodes with no or one parents. The graph is input as a single string in form of an array of (parent,child) pairs. Press enter to convert and generate the graph. The class method countNumberofParents() is then called that traverses the parents for each node using Breadth First Traversal and returns nodes with zero or one parent. A sample run for the task is shown in screenshot below.

<img src="/assets/img/projects/rest-api-project/algorithm01.jpeg" width="60%" />

## Working of Task 02

Given a graph and a node-pair present in the graph as input, the task is to find if the node-pair share atleast one common ancestor. Similar to task 01, the graph is input as a single String in form of an array of `(parent,child)` pairs. Press enter and then input node-pair present in the graph as a String. Press enter again to generate the graph and find common ancestors of the node-pair. The graph is traversed using  `Breadth First Traversal` to find the ancestors of specified node-pair and returns `true` if they have at least one common ancestor otherwise `false`. A sample run of the task is shown in screenshot below

<img src="/assets/img/projects/rest-api-project/algorithm02.jpeg" width="60%" />

## Sending requests to the API

A chrome extension [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en) is used for sending API requests.
Data is sent using `Post`requests to the API. The input is a json object with 2 fields `inputArray` and `nodePair`. The `inputArray` is the graph input that consists of an array of (parent,child) pairs, which is passed as string to the API. The `nodePair` is pair of two nodes present in the graph that is used to identify if they share common ancestor.

For Task 1, the API url is `http://localhost:8080/algorithm01`

A sample request is shown in figure below. Only `inputArray` field is required and `nodePair` is sent as empty string. The API returns 2 lists `Zero parent` and  `One parent` that specifies number of nodes having no parent and one parent respectively.

```json
{
    "inputArray": "{ {10, 3}, {2, 3},{3, 6}, { 5, 6},{5, 7},{4, 5},{4, 8},{8, 9} }",
    "nodePair": ""
}

```
<p float="center">
  <img src="/assets/img/projects/rest-api-project/task01.JPG" width="100%" />
</p>

For Task 2, the API url is `http://localhost:8080/algorithm02`. Both `inputArray` field as well as `nodePair` are required. The API returns boolean value that specifies if the nodes in `nodePair` share at least one common ancestor.

A sample request is shown in figure below, 

```json
{
	"inputArray": "{ {10, 3}, {2, 3},{3, 6}, { 5, 6},{5, 7},{4, 5},{4, 8},{8, 9} }",
	"nodePair": "3,8"
}
```
<p float="center">
  <img src="/assets/img/projects/rest-api-project/task02.JPG" width="100%" />
</p>