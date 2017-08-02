# Conversion Classes

## ArrayConv

ArrayConv is a utility used to help slice out arrays out of arrays without cloning them in memory. It was extended upon org.apache.commons.lang3.ArrayUtils.

See: https://commons.apache.org/proper/commons-lang/apidocs/org/apache/commons/lang3/ArrayUtils.html


{% hint style='info' %}
**ArrayConv History**

Initially ArrayConv had a lot more functions until Apache's latest updates which included the functions we required, but is still kept in case of future uses.

{% endhint %}


## BaseX

With reference to https://en.wikipedia.org/wiki/Base64, but not used as such. Similarly it is used to convert values sets (like UUID) into a format that can be safely transmitted over the internet / is readable.

BaseX acts as our library's foundational constructor for the creation of a unique/custom character set (charset). It is not built for performance on large input streams (20 bytes and above) as input values are collected internally into a BigInteger.

### Base62

Base62 is the custom charset created consisting the characters of 'A-Z', 'a-z', '0-9' and omitting characters '+', '='.

{% hint style='Working' %}
**Base62 Default Charset**

+ A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
+ a b c d e f g h i j k l m n o p q r s t u v w x y z
+ 0 1 2 3 4 5 6 7 8 9

{% endhint %}

### Base58

Base58 is the custom charset created to be used in cases where objects require characters susceptible to human identification error such as 'O';'0', 'I';'l' (which display very similarly when rendered). Consist of characters "A-Z" omitting 'O', "a-z" omitting 'l' and '1-9' omitting '0'.

The default charset is based off bitcoin base58 charset, as explained on :http://en.wikipedia.org/wiki/Base58

{% hint style='Working' %}
**Base58 Default Charset**

+ A B C D E F G H I J K L M N P Q R S T U V W X Y Z
+ a b c d e f g h i j k m n o p q r s t u v w x y z
+ 1 2 3 4 5 6 7 8 9

{% endhint %}

## ConvertJSON

ConvertJSON is a JSON simplifier which can be used to convert input maps, arrays, lists and objects into JSON strings and vice versa.

Examples of methods (from input to JSON string):

+ fromMap, fromList, fromObject, fromArray

(from JSON string to input structure):

+ toMap, toList, toObject, toCustomClass, toObjectArray, toStringArray, toDoubleArray, toIntArray, toFloatArray, toLongArray

### ConvertJSON.InvalidFormatJSON

Illegal JSON format type. Used to handle all format exceptions in this class.

Can be treated as a RuntimeException, and IllegalArgumentException.

## ConvertXML

ConvertXML is a XML simplifier which can be used to convert XML strings to a structure.

Examples of methods (from XML string to structure):

+ toMap, toCollapsedMap

### ConvertXML.InvalidFormatXML

Illegal JSON format type. Used to handle all format exceptions in this class.

Can be treated as a RuntimeException, and IllegalArgumentException.

## DateConv

DateConv acts as the library's convenience class to convert between date types. The default date format is DD-MM-YYYY.

## GenericConvert

Core class for all the common variable / primitive type conversions.

Its pattern is inherited into all the GenericConvert struct classes, allows for easy access to variable converters. This has since been split into 2 additional sub-classes. However as this main class inherits them all anyway, it is highly recommended to simply use this class instead.

This split is was done to simplify code maintenance of this package.

Methods include:

+ 'to', 'fetch', 'split', 'normalize'

{% hint style='Working' %}
**Example of method**

toGenericConvertList conversion of generic object

Performs the following strategies in the following order

+ No conversion (if its a GenericConvertList)
+ To GenericConvertList (if its a List)
+ toList -> GenericConvertList conversion
+ Fallback

<b>public static <V> GenericConvertList<V> toGenericConvertList(java.lang.Object input,
                                                             java.lang.Object fallbck)</b>

where,
+ input = input value to convert
+ fallbck = the fallback default

and returning the converted value.

{% endhint %}

## GUID

Provide several Globally Unique Identifier (GUID) functionalities. Namely paired with other conversion classes, input with the Unique GUID Value (UUID) to return a UUId object and arrays.

{% hint style='Working' %}
**Example of method**

Paired with Base64

<b>public static java.lang.String base64()</b>

with,

+ parameters: UUID - Unique GUID value

returns <i>a random 22 character base64 GUID string.</i>


{% endhint %}

## ListValueConv

A utility conversion class to help convert Map values from one type to another, such as to strings or string arrays.

Example of methods:

+ objectListToStringArray
+ objectToString
+ deduplicateValuesWithoutArrayOrder
+ toStringSet



## MapValueConv

## NestedObject

## RegexUtil

## StringEscape
