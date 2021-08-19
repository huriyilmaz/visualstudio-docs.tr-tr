---
title: Kod Parçacığı İşlevleri
description: C# kod parçacıklarıyla kullanılabilen GenerateSwitchCases(EnumerationLiteral), ClassName() ve SimpleTypeName(TypeName) işlevlerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3e941f7975d0be7116d316aea79b7e8580a64426
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056400"
---
# <a name="code-snippet-functions"></a>Kod parçacığı işlevleri

C# kod parçacıklarıyla kullanılabilen üç işlev vardır. İşlevler kod [parçacığının İşlev](../ide/code-snippets-schema-reference.md#function-element) öğesinde belirtilir. Kod parçacıkları oluşturma hakkında bilgi için bkz. [Kod parçacıkları.](../ide/code-snippets.md)

## <a name="functions"></a>İşlevler

Aşağıdaki tabloda kod parçacıklarındaki öğesiyle birlikte kullanılabilen `Function` işlevler açıkmektedir.

|İşlev|Açıklama|Dil|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|parametresi tarafından belirtilen numaralama üyeleri için bir switch deyimi ve bir dizi büyük/küçük harf deyimi `EnumerationLiteral` üretir. parametresi, bir sabit değer sabit değerine veya bir sabit değer `EnumerationLiteral` türüne başvuru olmalıdır.|C#|
|`ClassName()`|Eklenen kod parçacığını içeren sınıfın adını döndürür.|C#|
|`SimpleTypeName(TypeName)`|*TypeName parametresini* kod parçacığının çağrıldığında en basit biçimine azaltır.|C#|

## <a name="generateswitchcases-example"></a>GenerateSwitchCases örneği

Aşağıdaki örnekte işlevinin nasıl kullanımına sahip olduğu `GenerateSwitchCases` gösterir. Bu kod parçacığı ekildiğinde ve sabit değere bir sabit değer girildiğinde sabit değer, sabit değerde yer alan her değer için `$switch_on$` `$cases$` bir deyim `case` üretir.

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

Aşağıdaki örnekte işlevinin nasıl kullanımına sahip olduğu `ClassName` gösterir. Bu kod parçacığı ekildiğinde değişmez kod, kod dosyasındaki o konumdaki kapsayan `$classname$` sınıfın adıyla değiştirilir.

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

Bu örnek, işlevinin nasıl `SimpleTypeName` kullanılagelmektedir. Bu kod parçacığı bir kod dosyasına ekildiğinde değişmez kod, kod parçacığının çağrıldığında türün en basit `$SystemConsole$` <xref:System.Console> biçimiyle değiştirilir.

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

- [İşlev öğesi](../ide/code-snippets-schema-reference.md#function-element)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
