---
title: Web performans testi için özel bir ayıklama kuralı kodlama
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9aeb80d348e31de0934d515754c59346fac3c2ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665255"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Web performans testi için özel bir ayıklama kuralı kodlayın

Kendi ayıklama kurallarınızı oluşturabilirsiniz. Bunu yapmak için, bir ayıklama kuralı sınıfından kendi kurallarınızı türetirsiniz. Ayıklama kuralları <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> temel sınıfından türetilir.

> [!NOTE]
> Ayrıca, özel doğrulama kuralları da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Özel bir ayıklama kuralı oluşturmak için

1. Web performans testi içeren bir test projesi açın.

2. Seçim Ayıklama kuralınızı depolayabileceği ayrı bir sınıf kitaplığı projesi oluşturun.

    > [!IMPORTANT]
    > Bu sınıfı, testlerinizin bulunduğu projede oluşturabilirsiniz. Ancak, kuralı yeniden kullanmak istiyorsanız, kuralınızı depolayabileceği ayrı bir sınıf kitaplığı projesi oluşturmak daha iyidir. Ayrı bir proje oluşturursanız, bu yordamdaki isteğe bağlı adımları tamamlamalısınız.

3. Seçim Sınıf kitaplığı projesinde, Microsoft. VisualStudio. QualityTools. WebTestFramework DLL dosyasına bir başvuru ekleyin.

4. @No__t_0 sınıfından türeten bir sınıf oluşturun. @No__t_0 ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*> üyelerini uygulayın.

5. Seçim Yeni sınıf kitaplığı projesi oluşturun.

6. Seçim Test projesinde, özel ayıklama kuralını içeren sınıf kitaplığı projesine bir başvuru ekleyin.

7. Test projesinde, **Web Performans Testi Düzenleyicisi**bir Web başarım testi açın.

8. Özel ayıklama kuralı eklemek için, bir Web başarım testi isteğine sağ tıklayıp **ayıklama kuralı ekle**' yi seçin.

     **Ayıklama kuralı ekle** iletişim kutusu görünür. Özel doğrulama kuralınızı **bir kural seçin** listesinde, önceden tanımlanmış doğrulama kurallarıyla birlikte görürsünüz. Özel ayıklama kuralınızı seçin ve ardından **Tamam**' ı seçin.

9. Web performans testinizi çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod, özel bir ayıklama kuralının bir uygulamasını gösterir. Bu ayıklama kuralı belirtilen giriş alanından değeri ayıklar. Bu örneği kendi özel ayıklama kurallarınız için bir başlangıç noktası olarak kullanın.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

@No__t_0 yöntemi, bir ayıklama kuralının temel işlevlerini içerir. Önceki örnekteki <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> yöntemi, bu ayıklama kuralının kapsamasıyla oluşturulan yanıtı sağlayan bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> alır. Yanıt, yanıttaki tüm etiketleri içeren bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> içeriyor. Giriş etiketleri <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> filtrelenmez. Her giriş etiketi, değeri, `Name` özelliğinin Kullanıcı tarafından sağlanan değerine eşit olan `name` adlı bir öznitelik için incelenir. Bu eşleşen özniteliğe sahip bir etiket bulunursa, bir değer özniteliği varsa `value` özniteliği tarafından içerilen bir değeri ayıklamak için bir girişimde bulunuldu. Varsa, etiketin adı ve değeri çıkarılır ve Web performans testi bağlamına eklenir. Ayıklama kuralı geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Web performans testi için özel doğrulama kuralı kodlama](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)