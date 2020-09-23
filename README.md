<div align="center">

## Sort Data Table


</div>

### Description

Sort table data using javascript.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[masterp](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/masterp.md)
**Level**          |Intermediate
**User Rating**    |4.0 (8 globes from 2 users)
**Compatibility**  |
**Category**       |[Links](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/links__2-79.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/masterp-sort-data-table__2-2711/archive/master.zip)





### Source Code

```
<html>
<HEAD>
<SCRIPT LANGUAGE="JavaScript">
<!-- Begin
function setDataType(cValue)
 {
  // THIS FUNCTION CONVERTS DATES AND NUMBERS FOR PROPER ARRAY
  // SORTING WHEN IN THE SORT FUNCTION
  var isDate = new Date(cValue);
  if (isDate == "NaN")
   {
    if (isNaN(cValue))
     {
      // THE VALUE IS A STRING, MAKE ALL CHARACTERS IN
      // STRING UPPER CASE TO ASSURE PROPER A-Z SORT
      cValue = cValue.toUpperCase();
      return cValue;
     }
    else
     {
      // VALUE IS A NUMBER, TO PREVENT STRING SORTING OF A NUMBER
      // ADD AN ADDITIONAL DIGIT THAT IS THE + TO THE LENGTH OF
      // THE NUMBER WHEN IT IS A STRING
      var myNum;
      myNum = String.fromCharCode(48 + cValue.length) + cValue;
      return myNum;
     }
    }
 else
   {
    // VALUE TO SORT IS A DATE, REMOVE ALL OF THE PUNCTUATION AND
    // AND RETURN THE STRING NUMBER
    //BUG - STRING AND NOT NUMERICAL SORT .....
    // ( 1 - 10 - 11 - 2 - 3 - 4 - 41 - 5 etc.)
    var myDate = new String();
    myDate = isDate.getFullYear() + " " ;
    myDate = myDate + isDate.getMonth() + " ";
    myDate = myDate + isDate.getDate(); + " ";
    myDate = myDate + isDate.getHours(); + " ";
    myDate = myDate + isDate.getMinutes(); + " ";
    myDate = myDate + isDate.getSeconds();
    //myDate = String.fromCharCode(48 + myDate.length) + myDate;
    return myDate ;
   }
 }
function sortTable(col, tableToSort)
 {
  var iCurCell = col + tableToSort.cols;
  var totalRows = tableToSort.rows.length;
  var bSort = 0;
  var colArray = new Array();
  var oldIndex = new Array();
  var indexArray = new Array();
  var bArray = new Array();
  var newRow;
  var newCell;
  var i;
  var c;
  var j;
  // ** POPULATE THE ARRAY colArray WITH CONTENTS OF THE COLUMN SELECTED
  for (i=1; i < tableToSort.rows.length; i++)
   {
    colArray[i - 1] = setDataType(tableToSort.cells(iCurCell).innerText);
    iCurCell = iCurCell + tableToSort.cols;
   }
  // ** COPY ARRAY FOR COMPARISON AFTER SORT
  for (i=0; i < colArray.length; i++)
   {
    bArray[i] = colArray[i];
   }
  // ** SORT THE COLUMN ITEMS
  //alert ( colArray );
  colArray.sort();
  //alert ( colArray );
  for (i=0; i < colArray.length; i++)
   { // LOOP THROUGH THE NEW SORTED ARRAY
    indexArray[i] = (i+1);
    for(j=0; j < bArray.length; j++)
     { // LOOP THROUGH THE OLD ARRAY
      if (colArray[i] == bArray[j])
       { // WHEN THE ITEM IN THE OLD AND NEW MATCH, PLACE THE
        // CURRENT ROW NUMBER IN THE PROPER POSITION IN THE
        // NEW ORDER ARRAY SO ROWS CAN BE MOVED ....
        // MAKE SURE CURRENT ROW NUMBER IS NOT ALREADY IN THE
        // NEW ORDER ARRAY
        for (c=0; c<i; c++)
         {
          if ( oldIndex[c] == (j+1) )
          {
           bSort = 1;
          }
           }
           if (bSort == 0)
            {
             oldIndex[i] = (j+1);
            }
             bSort = 0;
            }
     }
  }
 // ** SORTING COMPLETE, ADD NEW ROWS TO BASE OF TABLE ....
 for (i=0; i<oldIndex.length; i++)
  {
   newRow = tableToSort.insertRow();
   for (c=0; c<tableToSort.cols; c++)
    {
     newCell = newRow.insertCell();
     newCell.innerHTML = tableToSort.rows(oldIndex[i]).cells(c).innerHTML;
    }
   }
 //MOVE NEW ROWS TO TOP OF TABLE ....
 for (i=1; i<totalRows; i++)
  {
   tableToSort.moveRow((tableToSort.rows.length -1),1);
  }
 //DELETE THE OLD ROWS FROM THE BOTTOM OF THE TABLE ....
 for (i=1; i<totalRows; i++)
  {
   tableToSort.deleteRow();
  }
 }
// End -->
</script>
</HEAD>
<BODY>
<TABLE WIDTH="75%" BORDER=1 CELLSPACING=0 CELLPADDING=2 name="rsTable" id=rsTable cols=5 bordercolordark=ffffff bordercolorlight=000000 bgcolor=cccccc align=center>
<TR bgcolor=mediumblue>
<TD>
<A href="javascript:sortTable(0, rsTable);"><FONT color=white><B>ID</FONT></B></A>
</TD>
<TD>
<A href="javascript:sortTable(1, rsTable);"><FONT color=white><B>NAME</FONT></B></A>
</TD>
<TD>
<A href="javascript:sortTable(2, rsTable);"><FONT color=white><B>DATE</FONT></B></A>
</TD>
<TD>
<A href="javascript:sortTable(3, rsTable);"><FONT color=white><B>PHONE</FONT></B></A>
</TD>
<TD>
<A href="javascript:sortTable(4, rsTable);"><FONT color=white><B>WORKFLOW</FONT></B></A>
</TD>
</TR>
</FONT>
<TR>
<TD>1</TD>
<TD>Andy Berry</TD>
<TD>4/9/72</TD>
<TD>763-555-1212</TD>
<TD>REVIEW</TD>
</TR>
<TR>
<TD>2</TD>
<TD>Dan Developer</TD>
<TD>9/3/63</TD>
<TD>215-555-1400</TD>
<TD>SAME</TD>
</TR>
<TR>
<TD>3</TD>
<TD>John Javascript</TD>
<TD>3/4/71</TD>
<TD>612-555-0987</TD>
<TD>REVIEW</TD>
</TR>
<TR>
<TD>4</TD>
<TD>Jerry JSPage</TD>
<TD>8/2/71</TD>
<TD>215-555-7654</TD>
<TD>SAME</TD>
</TR>
<TR>
<TD>5</TD>
<TD>Mary Mainframe</TD>
<TD>3/28/70</TD>
<TD>763-555-8295</TD>
<TD>REVIEW</TD>
</TR>
<TR>
<TD>6</TD>
<TD>Elaine Ecommerce</TD>
<TD>2/28/29</TD>
<TD>612-555-1338</TD>
<TD>REVIEW</TD>
</TR>
<TR>
<TD>7</TD>
<TD>John Smith</TD>
<TD>12/31/00</TD>
<TD>610-555-0987</TD>
<TD>SAME</TD>
</TR>
<TR>
<TD>8</TD>
<TD>Candy Coder</TD>
<TD>4/1/70</TD>
<TD>000-555-9099</TD>
<TD>SAME</TD>
</TR>
<TR>
<TD>9</TD>
<TD>Pippy Long Stocking</TD>
<TD>1/1/30</TD>
<TD>613-555-1338</TD>
<TD>DIFFERENT</TD>
</TR>
<TR>
<TD>10</TD>
<TD>111222</TD>
<TD>2/2/01</TD>
<TD>345-555-7654</TD>
<TD>DIFFERENT</TD>
</TR>
<TR>
<TD>11</TD>
<TD>Apple Man</TD>
<TD>3/13/74</TD>
<TD>215-555-4043</TD>
<TD>DIFFERENT</TD>
</TR>
<TR>
<TD>12</TD>
<TD>Blonde</TD>
<TD>12/13/78</TD>
<TD>453-455-4593</TD>
<TD>DIFFERENT</TD>
</TR>
<TR>
<TD>13</TD>
<TD>Water Boy</TD>
<TD>1/23/94</TD>
<TD>278-135-4683</TD>
<TD>REVIEW</TD>
</TR>
<TR>
<TD>14</TD>
<TD>Spooner</TD>
<TD>6/11/72</TD>
<TD>816-564-6463</TD>
<TD>DIFFERENT</TD>
</TR>
<TR>
<TD>15</TD>
<TD>Gator</TD>
<TD>2/6/95</TD>
<TD>456-355-5333</TD>
<TD>REVIEW</TD>
</TR>
<TR>
<TD>16</TD>
<TD>Boink</TD>
<TD>8/19/62</TD>
<TD>343-565-0786</TD>
<TD>DIFFERENT</TD>
</TR>
<TR>
<TD>17</TD>
<TD>Qwert</TD>
<TD>9/9/55</TD>
<TD>388-257-2341</TD>
<TD>SAME</TD>
</TR>
<TR>
<TD>18</TD>
<TD>Poppy</TD>
<TD>6/15/71</TD>
<TD>490-228-3453</TD>
<TD>SAME</TD>
</TR><TR>
<TD>19</TD>
<TD>JJ Qty</TD>
<TD>1/25/82</TD>
<TD>453-234-9976</TD>
<TD>REVIEW</TD>
</TR><TR>
<TD>20</TD>
<TD>Spanky</TD>
<TD>2/10/76</TD>
<TD>227-885-9009</TD>
<TD>SAME</TD>
</TR>
</TABLE>
</body>
</html>
```

