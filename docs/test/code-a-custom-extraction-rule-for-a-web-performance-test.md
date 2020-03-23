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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cce705135daa8bc54a7fab301cf5dcd8cf96d6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591183"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Web performans testi için özel bir çıkarma kuralı kodlama

Kendi çıkarma kurallarınızı oluşturabilirsiniz. Bunu yapmak için, bir çıkarma kuralı sınıfından kendi kurallarınızı türemişsiniz. Çıkarma kuralları taban <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> sınıftan türetilmiştir.

> [!NOTE]
> Özel doğrulama kuralları da oluşturabilirsiniz. Daha fazla bilgi için [bkz.](../test/create-custom-code-and-plug-ins-for-load-tests.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Özel bir çıkarma kuralı oluşturmak için

1. Web performans testi içeren bir Test projesi açın.

2. (İsteğe bağlı) Çıkarma kuralınızı depolamak için ayrı bir Sınıf kitaplığı projesi oluşturun.

    > [!IMPORTANT]
    > Sınıfı, testlerinizin içinde olduğu projede oluşturabilirsiniz. Ancak, kuralı yeniden kullanmak istiyorsanız, kuralınızı depolamak için ayrı bir Sınıf kitaplığı projesi oluşturmak daha iyidir. Ayrı bir proje oluşturursanız, bu yordamdaki isteğe bağlı adımları tamamlamanız gerekir.

3. (İsteğe bağlı) Sınıf kitaplığı projesinde, Microsoft.VisualStudio.QualityTools.WebTestFramework dll adresine bir başvuru ekleyin.

4. <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> Sınıftan türeyen bir sınıf oluşturun. Uygulayın <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*> ve üyeleri.

5. (İsteğe bağlı) Yeni Sınıf kitaplığı projesini oluşturun.

6. (İsteğe bağlı) Test projesinde, özel çıkarma kuralını içeren Sınıf kitaplığı projesine bir başvuru ekleyin.

7. Test projesinde, Web Performans Test **Web Performance Test Editor**Düzenleyicisi'nde bir web performans testi açın.

8. Özel çıkarma kuralını eklemek için, bir web performans testi isteğine sağ tıklayın ve **Ekstraksiyon Kuralı Ekle'yi**seçin.

     **Çıkarma Kuralı Ekle** iletişim kutusu görüntülenir. Özel doğrulama kuralınızı, önceden tanımlanmış doğrulama kurallarıyla birlikte bir kural listesi **seç'te** görürsünüz. Özel çıkarma kuralınızı seçin ve ardından **Tamam'ı**seçin.

9. Web performans testinizi çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod, özel bir çıkarma kuralının uygulanmasını gösterir. Bu çıkarma kuralı, belirtilen bir giriş alanından değeri ayıklar. Bu örneği, kendi özel çıkarma kurallarınız için bir başlangıç noktası olarak kullanın.

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

Yöntem, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> bir çıkarma kuralının temel işlevselliğini içerir. Önceki <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> örnekte yöntem, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> bu çıkarma kuralının kapsadığı istek tarafından oluşturulan yanıtı sağlayan bir yöntem alır. Yanıt, yanıttaki tüm etiketleri içeren bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> yanıt içerir. Giriş <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>etiketleri' nin dışına filtre lenir. Her giriş etiketi, değeri özelliğin `name` kullanıcı tarafından sağlanan değerine `Name` eşit olan bir öznitelik için incelenir. Bu eşleşen öznitelik ile bir etiket bulunursa, bir değer özniteliği `value` varsa, öznitelik tarafından bulunan bir değer ayıklamak için bir girişimyapılır. Varsa, etiketin adı ve değeri ayıklanır ve web performans testi bağlamına eklenir. Çıkarma kuralı geçer.

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
