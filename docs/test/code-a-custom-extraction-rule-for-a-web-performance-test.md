---
title: Özel ayıklama kuralı kodla (web perf testi)
description: Ayıklama kuralı sınıfından türetilen Kendi ayıklama kurallarınızı (ExtractionRule) oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: e3994d5cb15ef25c1f9915e1121d1c935ab18b84e0a5041c587447b022fa4153
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384970"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Web performans testi için özel ayıklama kuralı kodla

Kendi ayıklama kurallarınızı oluşturabilirsiniz. Bunu yapmak için bir ayıklama kuralı sınıfından kendi kurallarınızı türetirsiniz. Ayıklama kuralları temel sınıftan <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> türetildi.

> [!NOTE]
> Özel doğrulama kuralları da oluşturabilirsiniz. Daha fazla bilgi için [bkz. Yük testleri için özel kod ve eklentiler oluşturma.](../test/create-custom-code-and-plug-ins-for-load-tests.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Özel ayıklama kuralı oluşturmak için

1. Web performans testi içeren bir Test projesi açın.

2. (İsteğe bağlı) Ayıklama kuralınızı depolamak için ayrı bir Sınıf kitaplığı projesi oluşturun.

    > [!IMPORTANT]
    > Sınıfını, testlerinizi içinde olduğu projede oluşturabilirsiniz. Ancak, kuralı yeniden kullanmak için kuralınızı depolamak üzere ayrı bir Sınıf kitaplığı projesi oluşturmanız daha iyi olur. Ayrı bir proje sanız, bu yordamda isteğe bağlı adımları tamamlamanız gerekir.

3. (İsteğe bağlı) Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework dll dosyası için bir başvuru ekleyin.

4. sınıfından türeten bir sınıf <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> oluşturun. ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> üyelerini <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*> uygulama.

5. (İsteğe bağlı) Yeni Sınıf kitaplığı projesini derleme.

6. (İsteğe bağlı) Test projesine özel ayıklama kuralını içeren Sınıf kitaplığı projesine bir başvuru ekleyin.

7. Test projesinde, web'de bir web performans testi **Web Performans Testi Düzenleyicisi.**

8. Özel ayıklama kuralını eklemek için bir web performans testi isteğine sağ tıklayın ve Ayıklama Kuralı **Ekle'yi seçin.**

     Ayıklama **Kuralı Ekle iletişim** kutusu görüntülenir. Özel doğrulama kuralınızı Önceden tanımlanmış **doğrulama kurallarıyla** birlikte Kural seçin listesinde görünür. Özel ayıklama kuralınızı ve ardından Tamam'ı **seçin.**

9. Web performans testini çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod, özel ayıklama kuralının uygulamasını gösterir. Bu ayıklama kuralı, belirtilen giriş alanından değeri ayıklar. Kendi özel ayıklama kurallarınız için başlangıç noktası olarak bu örneği kullanın.

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

yöntemi, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> ayıklama kuralının temel işlevlerini içerir. Önceki <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> örnekteki yöntemi, bu ayıklama <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> kuralının kapsaması isteği tarafından oluşturulan yanıtı sağlayan bir alır. Yanıt, <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> yanıtta tüm etiketleri içeren bir içerir. Giriş etiketleri içinde <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> filtrelenmiş. Her giriş etiketi, değeri özelliğin kullanıcı tarafından sağlanan değerine eşit `name` adlı bir öznitelik için `Name` incelendi. Bu eşleşen öznliğe sahip bir etiket bulunursa, bir değer özniteliği varsa, özniteliğin içerdiği bir değeri `value` ayıklamaya çalışıldı. Varsa etiketin adı ve değeri ayıklanır ve web performansı testi bağlamına eklenir. Ayıklama kuralı geçer.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Web performans testi için özel bir doğrulama kuralı kodlama](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
