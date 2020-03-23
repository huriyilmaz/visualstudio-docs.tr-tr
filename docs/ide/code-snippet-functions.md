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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594246"
---
# <a name="code-snippet-functions"></a>Kod parçacığı işlevleri

C# kod parçacıkları ile kullanılabilecek üç işlev vardır. İşlevler kod snippet'in [İşlev](../ide/code-snippets-schema-reference.md#function-element) öğesinde belirtilir. Kod parçacıkları oluşturma hakkında daha fazla bilgi için [Kod parçacıklarına](../ide/code-snippets.md)bakın.

## <a name="functions"></a>İşlevler

Aşağıdaki tabloda kod parçacıkları öğesi `Function` ile kullanılmak üzere kullanılabilir işlevleri açıklanır.

|İşlev|Açıklama|Dil|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|`EnumerationLiteral` Parametre tarafından belirtilen numaralandırma üyeleri için bir anahtar deyimi ve örnek ifadeler kümesi oluşturur. Parametre, `EnumerationLiteral` numaralandırma edebi veya numaralandırma türüne bir başvuru olmalıdır.|C#|
|`ClassName()`|Eklenen parçacık içeren sınıfın adını döndürür.|C#|
|`SimpleTypeName(TypeName)`|*TypeName* parametresini, parçacığın çağrıldığı bağlamda en basit biçimine indirir.|C#|

## <a name="generateswitchcases-example"></a>GenerateSwitchCases örneği

Aşağıdaki örnek, işlevin `GenerateSwitchCases` nasıl kullanılacağını gösterir. Bu parçacık eklendiğinde ve bir numaralandırma `$switch_on$` gerçek içine girildiğinde, `$cases$` gerçek numaralandırmadaki her `case` değer için bir ifade oluşturur.

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

Aşağıdaki örnek, işlevin `ClassName` nasıl kullanılacağını gösterir. Bu parçacık eklendiğinde, `$classname$` literal kod dosyasındaki o konumdaki ençevreleyen sınıfın adı ile değiştirilir.

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

Bu örnek, işlevin `SimpleTypeName` nasıl kullanılacağını gösterir. Bu parçacık bir kod dosyasına eklendiğinde, `$SystemConsole$` snippet çağrıldı bağlamında <xref:System.Console> tür en basit formu ile literal değiştirilir.

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

- [Fonksiyon öğesi](../ide/code-snippets-schema-reference.md#function-element)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
