---
title: Kod Parçacığı İşlevleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7df85c429794d61028d5304108d289dfe9bf496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594246"
---
# <a name="code-snippet-functions"></a>Kod parçacığı işlevleri

C# kod parçacıkları ile kullanabileceğiniz üç işlev mevcuttur. İşlevler, kod parçacığının [Function](../ide/code-snippets-schema-reference.md#function-element) öğesinde belirtilir. Kod parçacıkları oluşturma hakkında daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

## <a name="functions"></a>İşlevler

Aşağıdaki tabloda, `Function` kod parçacıkları içindeki öğesiyle birlikte kullanılabilecek işlevler açıklanmaktadır.

|İşlev|Açıklama|Dil|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Parametresi tarafından belirtilen numaralandırma üyeleri için bir switch deyimi ve Case deyimleri kümesi oluşturur `EnumerationLiteral` . `EnumerationLiteral`Parametre, sabit listesi sabit değerine veya bir numaralandırma türüne başvuru olmalıdır.|C#|
|`ClassName()`|Eklenen kod parçacığını içeren sınıfın adını döndürür.|C#|
|`SimpleTypeName(TypeName)`|*TypeName* parametresini, kod parçacığının çağrıldığı bağlamdaki en basit biçimine düşürür.|C#|

## <a name="generateswitchcases-example"></a>GenerateSwitchCases örneği

Aşağıdaki örnek, işlevinin nasıl kullanılacağını gösterir `GenerateSwitchCases` . Bu kod parçacığı eklendiğinde ve sabit listesine bir sabit listesi girildiğinde `$switch_on$` , `$cases$` sabit `case` listesi Numaralandırmadaki her değer için bir ifade oluşturur.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="classname-example"></a>ClassName örneği

Aşağıdaki örnek, işlevinin nasıl kullanılacağını gösterir `ClassName` . Bu kod parçacığı eklendiğinde, `$classname$` değişmez değer, kod dosyasındaki bu konumdaki kapsayan sınıfın adı ile değiştirilmiştir.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="simpletypename-example"></a>SimpleTypeName örneği

Bu örnek, işlevinin nasıl kullanılacağını gösterir `SimpleTypeName` . Bu kod parçacığı bir kod dosyasına eklendiğinde, `$SystemConsole$` değişmez değer, <xref:System.Console> parçacığın çağrıldığı bağlamdaki türün en basit biçimiyle yerine geçer.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Function öğesi](../ide/code-snippets-schema-reference.md#function-element)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
