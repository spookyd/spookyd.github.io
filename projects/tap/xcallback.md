---
layout: page
title: Tap x-callback-url support
tags: portfolio
---

# x-callback-url

---

The following is based on the [x-callback-url specifications](http://x-callback-url.com/specifications/)

How the callback scheme is setup

`[scheme]://[host]/[action]?[x-callback parameters]&[action parameters]`

## Callback Support

### Scheme

Tap uses `tapApp` as the scheme.

### Actions

Tap supports the following actions

#### Get Counters

Gets all the counters

##### Action Name

`getCounters`

##### Parameters

> No parameters required

**Response Properties**

An array with properties
  - `counter` <- Array containing
    - `counterID`
    - `name`

##### Example Request

```
tapApp://x-callback-url/getCounters?
    x-success=sourceApp://x-callback-url/retrievedCounters&
    x-source=SourceApp&
    x-error=sourceApp://x-callback-url/getCountersError
```

##### Example Response

**Success**

```
sourceApp://x-callback-url/retrievedCounters?
    x-source=tapApp&
    counters=[{counterID: 0, name: "Test Counter"},{counterID: 1, name: "Another Counter"}]
```

> The counters property is left decoded for readability

#### Get Current Count

Gets the current count of the counter based on the id

##### Action Name

`getCurrentCount`

##### Parameters

  - counterID

**Response Properties**
  - `currentCount`

##### Example Request

```
tapApp://x-callback-url/getCurrentCount?
    x-success=sourceApp://x-callback-url/retrievedCurrentCount&
    x-source=SourceApp&
    x-error=sourceApp://x-callback-url/getCurrentCountError&
    counterID=1
```

##### Example Response

**Success**

```
sourceApp://x-callback-url/retrievedCurrentCount?
    x-source=tapApp&
    currentCount=13
```

#### Increment Counter

Increments the count of the counter based on the id

##### Action Name

`incrementCount`

##### Parameters

  - counterID

**Response Properties**
  - currentCount

##### Example Request

```
tapApp://x-callback-url/incrementCount?
    x-success=sourceApp://x-callback-url/acceptedIncrement&
    x-source=SourceApp&
    x-error=sourceApp://x-callback-url/incrementError&
    counterID=1
```

##### Example Response

**Success**

```
sourceApp://x-callback-url/acceptedIncrement?
    x-source=tapApp&
    currentCount=13
```

#### Decrement Counter

Decrements the count of the counter based on the id

##### Action Name

`decrementCount`

##### Parameters

  - counterID

**Response Properties**
  - currentCount

##### Example Request

```
tapApp://x-callback-url/decrementCount?
    x-success=sourceApp://x-callback-url/acceptedDecrement&
    x-source=SourceApp&
    x-error=sourceApp://x-callback-url/decrementError&
    counterID=1
```

##### Example Response

**Success**

```
sourceApp://x-callback-url/acceptedDecrement?
    x-source=tapApp&
    currentCount=13
```

#### Reset Counter

Resets the count of the counter based on the id

##### Action Name

`resetCount`

##### Parameters

  - counterID

**Response Properties**
  - none

##### Example Request

```
tapApp://x-callback-url/resetCount?
    x-success=sourceApp://x-callback-url/acceptedReset&
    x-source=SourceApp&
    x-error=sourceApp://x-callback-url/resetError&
    counterID=1
```

##### Example Response

**Success**

```
sourceApp://x-callback-url/acceptedReset?
    x-source=SourceApp
```

### x-callback parameters

`x-source` - Required for caller identification
`x-success` - Used to return the results on success
`x-error` - Used to return on error

### Error Responses

#### Properties

  - `errorCode`
  - `errorMessage`

#### Missing Source App Identifier

**Code:** 1320

**Description:** The `sourceApp` property is required

#### Missing Required Property

**Code:** 1321

**Description:** Property [missing property] is required

#### Unknown Counter

**Code:** 1501

**Description:** The id used in the parameter could not be located

#### Generic Action Failure

**Code:** 1505

**Description:** [Action] could not be performed on counter with id: [counterID]

#### Decrement Action Failure at minimum value

**Code:** 1510

**Description:** Could not decrement counter [counterID]. Already at minimum value