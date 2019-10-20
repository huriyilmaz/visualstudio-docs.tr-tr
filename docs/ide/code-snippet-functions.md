---
title: Kod Parçacığı İşlevleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85124837e378ea4377de0ca08c5a8680034240c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647537"
---
# <a name="code-snippet-functions"></a>Kod parçacığı işlevleri

Kod parçacıkları ile C# kullanabileceğiniz üç işlev mevcuttur. İşlevler, kod parçacığının [Function](../ide/code-snippets-schema-reference.md#function-element) öğesinde belirtilir. Kod parçacıkları oluşturma hakkında daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

## <a name="functions"></a>İşlevler

Aşağıdaki tabloda, kod parçacıkları içinde `Function` öğesiyle birlikte kullanılabilecek işlevler açıklanmaktadır.

|İşlev|Açıklama|Dil|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|@No__t_0 parametresi tarafından belirtilen numaralandırma üyeleri için bir switch deyimi ve Case deyimleri kümesi oluşturur. @No__t_0 parametresi bir sabit listesi sabit değeri ya da bir numaralandırma türü için başvuru olmalıdır.|C#|
|`ClassName()`|Eklenen kod parçacığını içeren sınıfın adını döndürür.|C#|
|`SimpleTypeName(TypeName)`|*TypeName* parametresini, kod parçacığının çağrıldığı bağlamdaki en basit biçimine düşürür.|C#|

## <a name="generateswitchcases-example"></a>GenerateSwitchCases örneği

Aşağıdaki örnek, `GenerateSwitchCases` işlevinin nasıl kullanılacağını göstermektedir. Bu kod parçacığı eklendiğinde ve `$switch_on$` değişmez değerine bir numaralandırma girildiğinde, `$cases$` değişmez değeri, Numaralandırmadaki her değer için bir `case` açıklaması oluşturur.

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

Aşağıdaki örnek, `ClassName` işlevinin nasıl kullanılacağını göstermektedir. Bu kod parçacığı eklendiğinde `$classname$` değişmez değeri, kod dosyasındaki bu konumdaki kapsayan sınıfın adı ile değiştirilmiştir.

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

Bu örnek, `SimpleTypeName` işlevinin nasıl kullanılacağını gösterir. Bu kod parçacığı bir kod dosyasına eklendiğinde `$SystemConsole$` değişmez değeri, parçacığın çağrıldığı bağlamdaki <xref:System.Console> türünün en basit biçimiyle yerine geçer.

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
