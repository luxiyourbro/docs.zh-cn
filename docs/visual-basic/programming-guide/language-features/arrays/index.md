---
title: Visual Basic 中的数组
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b6c1db0131f2a150dc1b00dd5e6dafc3a418f05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="arrays-in-visual-basic"></a>Visual Basic 中的数组
数组是一组值，称为*元素*，逻辑上彼此相关。 例如，数组可能包含的语法学校; 每个年级的学生的数量数组的每个元素是单个年级的学生的数量。 同样，数组可能包含的类，则的学生成绩数组的每个元素是单个评分。    

它是可能的单个变量来存储每个数据项。 例如，如果我们的应用程序分析学生成绩，我们可以使用单独的变量的每个学生成绩，如`englishGrade1`， `englishGrade2`，等等。此方法具有三个主要限制：
- 我们必须知道在设计时，我们需要处理完全多少年级。
- 快速处理大量年级变得非常笨拙。 这反过来会使应用程序更可能有严重的 bug。
- 很难维护。 我们添加每个新年级，需要应用程序进行修改、 重新编译，并重新部署。  
 
 通过使用一个数组，你可以通过相同的名称，请参阅这些相关的值并使用一个数字，称为*索引*或*下标*若要确定基于数组中其位置的单个元素。 数组范围从 0 到减 1 所得的数组中的元素总数的索引。 当你使用 Visual Basic 语法来定义数组的大小时，你将指定其最高的索引，不的数组中的元素总数。 你可以使用作为一个单元中，数组和来循环访问其元素的功能使你无需知道它包含在设计时完全多少个元素。
  
 在进行说明之前，请看几个简单的示例：  
  
```vb  
' Declare a single-dimension array of 5 numbers.  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set its 4 values.  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)
  
' Redefine the size of an existing array and reset the values.
ReDim numbers(15)  
  
' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double  
  
' Declare a 4 x 3 multidimensional array and set array element values.  
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}  
  
' Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 ## <a name="in-this-article"></a>本文内容
  
- [简单数组中的数组元素](#array-elements-in-a-simple-array)  
  
- [创建的数组](#creating-an-array)  
  
- [将值存储在数组中](#storing-values-in-an-array)  
  
- [填充数组与数组文本](#populating-an-array-with-array-literals)  
  
- [循环访问数组](#iterating-through-an-array)  
  
- [数组大小](#BKMK_ArraySize)  

- [数组类型](#the-array-type)  
  
- [作为返回值和参数的数组](#arrays-as-return-values-and-parameters)  
- [交错的数组](#jagged-arrays)  
  
- [零长度数组](#zero-length-arrays)  

- [拆分数组](#splitting-an-array)
  
- [作为数组的替代方法的集合](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>简单数组中的数组元素  

让我们创建一个名为数组`students`存储语法学校中每个年级的学生的数量。 这些元素的索引范围为 0 到 6。 使用此数组是比声明七个变量更简单。

下图显示`students`数组。 对于数组的每个元素：  
  
-   元素索引表示年级（索引 0 表示幼儿园）。
  
-   元素中包含的值表示每个年级的学生数量。
  
 ![显示学生人数的数组图片](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif " ArrayExampleSchool ")  
“学生”数组中的元素  
 
下面的示例包含 Visual Basic 代码中创建和使用数组：

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

该示例执行三项操作：

- 它声明`students`具有七个元素的数组。 数`6`数组中声明指示数组中的最后一个索引; 它是一个小于数组中元素的数目。
- 它将值分配给数组中每个元素。 通过使用数组名称并在括号中包括单个元素的索引访问数组元素。
- 它将列出该数组的每个值。 该示例使用[ `For` ](../../../language-reference/statements/for-next-statement.md)语句可以访问该数组的每个元素按其索引号。
  
 `students`数组在前面的示例是一个一维数组，因为它使用一个索引。 使用多个索引或下标的数组称为*多维*。 有关详细信息，请参阅本文的其余部分和[在 Visual Basic 中的数组维数](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
##  <a name="creating-an-array"></a>创建数组  
 
你可以通过多种方式来定义非数组的大小： 

- 声明数组时，你可以指定大小：
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - 你可以使用`New`子句提供数组的大小，创建时：  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 如果你有现有数组，你可以通过使用来重新定义其大小[ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md)语句。 你可以指定`Redim`语句保留在阵列，值也可以指定它创建一个空数组。 下面的示例演示了用 `Redim` 语句来修改现有数组的大小的不同用法。  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 有关详细信息，请参阅[ReDim 语句](../../../../visual-basic/language-reference/statements/redim-statement.md)。  
  
##  <a name="storing-values-in-an-array"></a>存储数组中的值
 
 你可以通过使用类型 `Integer`的索引访问数组中的每个位置。 你可以使用括号内的索引来引用每个数组位置，从而存储和检索数组中的值。 对于多维数组的索引用逗号 （，） 分隔。 每个数组维度都需要一个索引。 

下面的示例演示用于存储和检索值在数组中的一些语句。
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>填充数组与数组文本
 通过使用数组文本，你可以创建它时填充一组初始的值的数组。 数组文本包含用逗号分隔的值列表，这些值被括在括号内 (`{}`)。  
  
 通过使用数组文本创建数组时，可以提供数组类型或使用类型推理功能来确定数组类型。 下面的示例演示这两个选项。  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 当你使用类型推理时，数组的类型由*基准类型*中的文本值列表。 基准类型是数组中的所有其他类型可以扩大到其中的类型。 如果无法确定此唯一类型，基准类型是数组中所有其他类型可以缩小到的唯一类型。 如果无法确定为这两种唯一类型之一，则基准类型是 `Object`。 例如，如果提供给数组文本的值的列表包含 `Integer`、 `Long`和 `Double`类型的值，则生成的数组类型是 `Double`。 因为`Integer`和`Long`都仅扩大到`Double`，`Double`是基准类型。 有关详细信息，请参阅 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。 
 
> [!NOTE] 
> 类型推理仅用于定义为类型成员中的本地变量的数组。 如果缺少显式类型定义，则使用数组文本，在类级别定义的数组是类型的`Object[]`。 有关详细信息，请参阅[局部类型推理](../variables/local-type-inference.md)。 

请注意，上面的示例定义`values`类型的数组作为`Double`即使所有数组文本的类型都是`Integer`。 您可以创建此数组，因为数组文本中的值可以扩大到`Double`值。 
  
 你还可以创建和使用填充多维数组*嵌套数组文本*。 嵌套的数组文本必须具有与生成的数组保持一致维度的数目。 下面的示例通过使用嵌套的数组文本创建二维整数数组。  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
在使用嵌套的数组文本创建并填充数组时，如果嵌套的数组文本中的元素的数目不匹配，则会发生错误。 如果你显式声明的数组变量具有不同数量的维度比数组文本，也会发生错误。 
  
就像可以对于一维数组，你可以依赖类型推断，使用嵌套的数组文本创建多维数组时。 推断出的类型是所有嵌套级别的所有数组文本中的所有值的基准类型。 下面的示例创建类型的一个二维数组`Double[,]`的类型的值从`Integer`和`Double`。  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 有关其他示例，请参阅[如何：在 Visual Basic 中初始化数组变量](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)。  
  
##  <a name="iterating-through-an-array"></a>循环访问数组  
 当循环访问数组时，你可以访问数组中的每个元素，从最低到最高或从高到低的顺序。 通常情况下，使用这两个使用[为...下一条语句](../../../../visual-basic/language-reference/statements/for-next-statement.md)或[每个...下一条语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)循环访问数组的元素。 如果您不知道数组的上限，可以调用<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>方法以获取索引的最高值。 虽然几乎是最低的索引值始终为 0，可以调用<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>方法以获取索引的最低值。   
  
 下面的示例循环访问一个一维数组使用[ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md)语句。 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 下面的示例循环访问一个多维数组使用[ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md)语句。 <xref:System.Array.GetUpperBound%2A> 方法具有用于指定维度的参数。 `GetUpperBound(0)` 返回的最高的第一个维度的索引和`GetUpperBound(1)`返回第二个维度的最高的索引。
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 下面的示例使用[每个...下一条语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)来循环访问一个一维数组和一个二维数组。  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>数组大小  

 数组的大小是数组所有维度的长度的产物。 它表示数组中当前所包含的元素总数。  例如，下面的示例声明每个维度中的四个元素的二维数组。 如示例输出所示，数组的大小为 16 (或 (3 + 1) * (3 + 1)。

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> 数组大小的这一讨论不适用于交错数组。 交错的数组并确定交错数组的大小的信息，请参阅[交错数组](#jagged-arrays)部分。
  
  可以通过使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 属性查找数组大小。 你可以通过使用查找每个维度的多维数组的长度<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。  
  
 可以调整一个数组变量的大小分配给它的新数组对象或使用[`ReDim`语句](../../../../visual-basic/language-reference/statements/redim-statement.md)语句。 下面的示例使用`ReDim`语句来切换到一个 51 元素的数组的一个 100 元素的数组。

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 当处理数组大小时，需要记住几件事情。  
  
|||  
|---|---|  
|维度长度|每个维度的索引是基于 0 的这意味着它范围从 0 到其上限。 因此，给定维度的长度是一个大于该维度的声明的上限。|  
|长度限制|每个维度的数组的长度最多的最大值`Integer`数据类型，即<xref:System.Int32.MaxValue?displayProperty=nameWithType>或 (2 ^31)-1。 但是，数组的总大小还受到系统上可用的内存限制。 如果你尝试初始化数组，超过了可用内存量，则运行时会引发<xref:System.OutOfMemoryException>。|  
|大小和元素大小|数组的大小独立于其元素的数据类型。 大小始终表示元素，不占用的内存的字节数的总数目。|  
|内存消耗|做出关于数组如何存储在内存中的假设是不可靠的。 由于不同数据宽度的平台上的存储会有所变化，因此同一数组在 64 位系统上可以占用比在 32 位系统上更多的内存。 具体取决于数组初始化时的系统配置，公共语言运行时 (CLR) 可以尽可能地将存储分配到靠近包元素的地方，或者将它们全部在自然硬件边界上对齐。 此外，数组需要存储开销的控制信息，而且每添加一个维度，这种开销随之增加。|  

## <a name="the-array-type"></a>数组类型 
 每个数组具有不同于其元素的数据类型的数据类型。 没有一种数据类型能用于所有数组。 相反，数组的数据类型由数组的维度数量或 *“排名”*，以及数组中元素的数据类型确定。 两个数组变量为相同的数据仅它们具有相同的排名且它们的元素具有相同的数据类型。 数组的维度的长度不会影响数组数据类型。  
  
 每个数组都继承自 <xref:System.Array?displayProperty=nameWithType> 类，并且你可以声明一个类型为 `Array` 的变量，但不能创建一个类型为 `Array` 的数组。 例如，尽管下面的代码声明`arr`变量的类型为`Array`和调用<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>方法可实例化的数组，数组的类型证明是对象 []。

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

此外，[ReDim 语句](../../../../visual-basic/language-reference/statements/redim-statement.md)无法对声明为类型 `Array` 的变量执行运算。 出于这些原因，以及为类型安全，则最好声明为特定类型的每个数组。  
  
 你可以通过几种方式了解到数组及其元素的数据类型。 
  
-   你可以调用<xref:System.Object.GetType%2A>方法变量以获取<xref:System.Type>表示变量的运行时类型的对象。 <xref:System.Type> 对象可在其属性和方法中保存大量信息。  
  
-   你可以将该变量传递到<xref:Microsoft.VisualBasic.Information.TypeName%2A>函数可获取`String`运行时类型的名称。  
  
 下面的示例调用同时`GetType`方法和`TypeName`函数来确定数组的类型。 数组类型是`Byte(,)`。 请注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType>属性还指示的字节数组的基类型是<xref:System.Array>类。  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>作为返回值和参数的数组  
 若要通过 `Function` 过程返回数组，请将数组数据类型和维度数指定为 [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)的返回类型。 在函数内，声明一个具有相同数据类型和维度数的本地数组变量。 在 [Return 语句](../../../../visual-basic/language-reference/statements/return-statement.md)中，添加不带括号的局部数组变量。  
  
 若要将作为参数的数组指定到 `Sub` 或 `Function` 步骤中，可将此参数定义为具有指定数据类型和维度数量的数组。 在调用的过程，将传递一个数组变量具有相同的数据类型和维度数。  
  
 在下面的示例中，`GetNumbers`函数返回`Integer()`，类型的一维数组`Integer`。 `ShowNumbers` 过程接受 `Integer()` 参数。 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 在下面的示例中，`GetNumbersMultiDim`函数返回`Integer(,)`，类型的一个二维数组`Integer`。  `ShowNumbersMultiDim` 过程接受 `Integer(,)` 参数。  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>交错数组  
 
有时应用程序中的数据结构是二维而不是矩形。 例如，可能使用一个数组来存储每一天的月的高温度有关的数据。 数组的第一个维度表示的月份，但第二个维度则表示的天数，并且在一个月天数不统一。 A*交错的数组*，这也称为*数组组成的数组*，专为这种情况。 交错的数组是一个数组，其元素也是数组。 交错数组和交错数组中的每个元素都可以具有一个或多个维度。  
  
 下面的示例使用月份数组，其中每个元素是天数数组。 该示例使用交错的数组，因为不同的月份具有不同数量的天数。  该示例演示如何创建交错的数组、 将值分配给它，并检索和显示其值。
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

前面的示例将值分配给元素的元素按交错数组，通过使用`For...Next`循环。 通过使用嵌套的数组文本，也可以将值分配给交错数组的元素。 但是，尝试使用嵌套数组文本 (例如， ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) 将生成编译器错误[BC30568](../../../,,/../misc/bc30568.md)。 若要更正错误，请用括号括起来将内部数组文本。 圆括号强制数组文字表达式进行计算，并将生成的值用于外部数组文本，如以下示例所示。  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

交错的数组是其元素包含数组的一维数组。 因此，<xref:System.Array.Length%2A?displayProperty=nameWithType>属性和`Array.GetLength(0)`方法返回的一维数组中的元素的数目和`Array.GetLength(1)`引发<xref:System.IndexOutOfRangeException>因为交错的数组不是多维。 检索的值的每个子数组确定每个子数组中的元素数<xref:System.Array.Length%2A?displayProperty=nameWithType>属性。 下面的示例演示如何确定交错数组中的元素数。

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>零长度数组  
Visual Basic 区分未初始化的数组 (其值是一个数组`Nothing`) 和一个*零长度数组*或空数组 （不包含任何元素的数组。）未初始化的数组是指不维度化或已分配给它的任何值。 例如：

```vb
Dim arr() As String
```
一个零长度数组声明一个尺寸为-1。 例如：

```vb
Dim arrZ(-1) As String
```
在下列情况下，你可能需要创建一个零长度数组：  
  
-   不会面临的风险的情况下<xref:System.NullReferenceException>异常，你的代码必须访问的成员<xref:System.Array>类，如<xref:System.Array.Length%2A>或<xref:System.Array.Rank%2A>，或如调用 Visual Basic 函数<xref:Microsoft.VisualBasic.Information.UBound%2A>。  
  
-   你想要保留你的代码，而不必检查简单`Nothing`作为一种特殊情况。  
  
-   你的代码与应用程序编程接口 (API) 交互，该接口要求你将一个零长度数组传递到一个或多个过程，或将一个零长度数组返回到一个或多个过程。

## <a name="splitting-an-array"></a>拆分数组

在某些情况下，你可能需要将单个数组拆分为多个阵列。 这涉及到标识点或从该处的数组是进行拆分，数据点，然后 spitting 到两个或多个单独的数组的数组。 

> [!NOTE] 
> 本部分不讨论将单个字符串拆分为基于某些分隔符的字符串数组。 有关将字符串拆分的信息，请参阅<xref:System.String.Split%2A?displayProperty=nameWithType>方法。

将拆分为数组的最常见条件是：

- 数组中的元素数。 例如，你可能想要拆分为多个相等部分大约的多个指定数量的元素数组。 为此，你可以使用通过以下任一方法返回的值<xref:System.Array.Length%2A?displayProperty=nameWithType>或<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。

- 元素，它可作为分隔符，该值指示应在何处拆分数组值。 可以在多用户环境中搜索特定值，通过调用<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>和<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>方法。
 
一旦确定或多个应从该处拆分数组的索引，然后可以通过调用创建单个数组<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。 

下面的示例将拆分为大小大约相等的两个数组的数组。 （如果数组元素的总数目为奇数，第一个数组具有多个元素的第二个。） 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

下面的示例将字符串数组拆分为两个数组根据其值是"zzz"，用作数组分隔符的元素存在。 新的阵列不包括包含分隔符的元素。

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>联接数组

你还可以将大量的数组组合到单个更大的阵列。 若要执行此操作，也使用<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。 

> [!NOTE] 
> 本部分不讨论连接成单个字符串的字符串数组。 有关联接的字符串数组的信息，请参阅<xref:System.String.Join%2A?displayProperty=nameWithType>方法。

在将每个数组的元素复制到新数组之前, 你首先必须确保，这样就足够大到 accompodate 新数组初始化数组。 可以通过两种方法执行此操作：

- 使用[ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md)动态展开数组，然后将新元素添加到它的语句。 这是最简单的技术，但它可能导致性能降低或过多的内存消耗复制大型数组时。
- 计算所需的新的大型数组的元素总数，然后向其添加每个源数组的元素。

下面的示例使用第二种方法添加到单个数组十个元素的四个阵列。  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

因为在这种情况下源数组也是所有小型，我们还可以动态地可以展开数组，我们将每个新数组的元素添加到它。 以下示例执行该操作。

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>作为数组的替代方法的集合  
 数组最适用于创建和使用固定数量的强类型化对象。 集合提供更灵活的方式来使用对象组。 与数组不同，这要求你显式更改数组的大小[`ReDim`语句](../../../../visual-basic/language-reference/statements/redim-statement.md)，集合增加和减少动态随着需求的应用程序更改。  
  
 当你使用`ReDim`来重新设置其维数的数组，Visual Basic 创建一个新数组和释放前一个。 这需要执行时间。 因此，如果你正在使用频繁变化，或者你的项目数无法预测你需要的项的最大数目，你通常将使用集合获得更好的性能。  
  
 对于某些集合，你可以为放入集合中的任何对象分配一个密钥，这样你便可以使用该密钥快速检索此对象。  
  
 如果你的集合中只包含一种数据类型的元素，你可以使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一个类。 泛型集合强制类型安全，因此无法向其添加任何其他数据类型。  
  
 有关集合的详细信息，请参阅[集合](../../concepts/collections.md)。
  
## <a name="related-topics"></a>相关主题  
  
|术语|定义|  
|----------|----------------|  
|[Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|在数组中解释级别和维度。|  
|[如何：在 Visual Basic 中初始化数组变量](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|说明如何用初始值填充数组。|  
|[如何：在 Visual Basic 中对数组进行排序](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|显示如何按字母先后顺序对数组元素进行排序。|  
|[如何：将一个数组赋给另一个数组](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|说明将数组分配到另一个数组变量的规则和步骤。|  
|[数组疑难解答](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|讨论在使用数组时出现的一些常见问题。|  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Array?displayProperty=nameWithType>  
 [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim 语句](../../../../visual-basic/language-reference/statements/redim-statement.md)
