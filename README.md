[ ![Download](https://api.bintray.com/packages/farhad/maven/irbill/images/download.svg) ](https://bintray.com/farhad/maven/irbill/_latestVersion) [![HitCount](http://hits.dwyl.io/the724/irbill.svg)](http://hits.dwyl.io/the724/irbill)

```groovy
repositories {
	jcenter()
}
	
implementation 'io.github.the724:irbill:[latest-version]'
```
---

For validating and parsing a barcode representing a bill, use the `parseBarcode()` method. 
```java
Bill bill = IrBill.parseBarcode("the-string-data-of-barcode") ;
```
If the barcode contains valid data, the `bill` object contains information such has billId, paymentId, amount and bill type. Otherwise the `bill` will be `null`.

In order to validate and parse `billId` and `paymentId`, also known as شناسه قبض  and  شناسه پرداخت, you can alternatively use the `parseBillData` method :

```java
Bill bill = IrBill.parseBillData("billId","paymentId");
```
If the billId and paymentId are valid, the `bill` object will contain more complementary information such as amount and bill type. Otherwise the `bill` will be `null`.

There are also two public utility methods, `validateBillId` and `validatePaymentId`, which can come handy for further debugging.

```java
if(IrBill.validateBillId("billId")) ...

if(IrBill.validatePaymentId("billId","paymentId")...
```

The `Bill` class has the following field members :

``` java
class Bill {

    private BillType type ;
    private String billId ;
    private String paymentId ;
    private long amount ; //in RIALS (IRR)
    
 }   
```

and the `BillType` enum contains information on different types of bills and their string representations in Persian and English.
<br/>

Finally, if the `paymentId` strings starts with leading zeroes, which is a typical case with bills of all types, **all** IrBill methods that accept `paymentId`, either directly or indirectly will take care of the trimming.

### License

    Copyright (C) 2018  Farhad Faghihi

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.