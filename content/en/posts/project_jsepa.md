+++
title = 'project jSEPA'
date = 2024-01-07T21:49:27+01:00
draft = true
+++

The project *jSEPA*[[1]]({{< ref "#jSEPA" >}}) was originally build and develop 
by an old college from me, with the goal to provide a Java library, 
which can create valid *SEPA*[[2]]({{< ref "#SEPA" >}})
`XML` documents for customer credit transfer initiations and customer direct debit initiations.
Both `XML` schemes are part of the *ISO 20022*[[3]]({{< ref "#ISO" >}}) standard.
If you are interested in more information about the standard, I strongly recommend 
you to read the message definitions of the *payment initiations*[[4]]({{< ref "#PI" >}}) 
section of the standard.

## why are we here?

*jSEPA* wanted to provide an easy to use interface, so that the developer was 
not forced to dive deep in the - lets say - challenging `XSD`. This goal seemed 
to have been achieved; well I mean achieved for the year 2014 - the year of 
the first commit. It came as it had to come, time goes by quicker as thought 
and no one updated or refactored the project. The code base is non-uniform, the 
API unclear, the way of solving problems questionable and I guess by far the biggest 
problem: the used `XSD` scheme versions are outdated and not anymore accepted by 
the banks. In a nutshell: the project is not usable.

## and now?

I am highly interested and a huge supporter of the **open source** idea / standard 
/ movement; but until now, I had some obstacles to contribute to bigger projects. 
Most of my time as a Java developer, I work on closed source projects more or 
less the full day. I want to change that. First things first: I want to clean up 
my handed over *jSEPA* project. 

### the plan

The `jSEPA` library has three basic features:

- providing an API to generate a customer credit transfer initiation `XML` document
- providing an API to generate a customer direct debit initiation `XML` document
- some utility functions regarding *BIC*[[5]]({{< ref "#BIC" >}}) and *IBAN*[[6]]({{< ref "#IBAN" >}})

For the first step, I want to clean up the existing code, without refactoring 
any existing functionality. This includes unused methods, unnecessary comments, unclear 
documentations and so on. 

After that, I want to abstract the API in interfaces, with a clear documentation, of 
what should do what and why, before I start touching the functionality of the code.


#### `XSLT` instead of `JAXB2` auto code generation

In the current implementation, the `jSEPA` project uses an auto generated data model, 
which is based on the (2014) given `XSD` schemes `PAIN_008_001_02` and `PAIN_001_003_03`. 
This approaches leads to a numerous amount of boilerplate code which is hard to 
understand, read methods or descriptions (to be fair, the `XSD` is here to blame).

To face this problem, my goal is to use a clean and easy to understand data model, 
which then will be transformed via a `XSLT` style-sheet to the target standardised 
`XML` file. This approach will help a lot in future updates to keep the API 
stable, since in most of the cases, only the `XSTL` need to be changed.

#### utility functions

The class `BankInformationStore` provides some static helper methods, which mostly 
communicates with the an "cache" (a simple Map) of `BankInformation` objects.
They store reference data of banks. Currently only German banks are supported. 
In the first step, I will leave this functionality untouched - until I decide, 
what should happen whit it. Feel free to open tickets on *GitHub*[[7]]({{< ref "#GitHub" >}}) 
if you have any ideas.



## references

- <span id="jSEPA">[1][https://github.com/JelmenGuhlke/jSEPA](https://github.com/JelmenGuhlke/jSEPA)
- <span id="SEPA">[2][https://en.wikipedia.org/wiki/Single_Euro_Payments_Area](https://en.wikipedia.org/wiki/Single_Euro_Payments_Area)
- <span id="ISO">[3][https://www.iso20022.org/](https://www.iso20022.org/)
- <span id="PI">[4][https://www.iso20022.org/iso-20022-message-definitions?search=Payments%20Initiation](https://www.iso20022.org/iso-20022-message-definitions?search=Payments%20Initiation)
- <span id="BIC">[5][https://www.swift.com/standards/data-standards/bic-business-identifier-code](https://www.swift.com/standards/data-standards/bic-business-identifier-code)
- <span id="IBAN">[6][https://www.swift.com/standards/data-standards/iban-international-bank-account-number](https://www.swift.com/standards/data-standards/iban-international-bank-account-number)
- <span id="GitHub">[7][https://github.com/JelmenGuhlke/jSEPA](https://github.com/JelmenGuhlke/jSEPA)
