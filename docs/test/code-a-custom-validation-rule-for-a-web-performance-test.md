---
title: Web perf testi için özel doğrulama kuralı oluşturma
description: ValidationRule doğrulama kuralı sınıfından türetilen kendi doğrulama kurallarınızı oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 5eb34377ab17bec9a1e8bb51e213eb24b7415e48
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026908"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>Web performans testi için özel doğrulama kuralı kodla

Kendi doğrulama kurallarınızı oluşturabilirsiniz. Bunu yapmak için, bir doğrulama kuralı sınıfından kendi kural sınıfını türetirsiniz. Doğrulama kuralları temel sınıftan <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> türetildi.

> [!NOTE]
> Özel ayıklama kuralları da oluşturabilirsiniz. Daha fazla bilgi için [bkz. Yük testleri için özel kod ve eklentiler oluşturma.](../test/create-custom-code-and-plug-ins-for-load-tests.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>Özel doğrulama kuralları oluşturmak için

1. Web performans testi Project test testini açın.

2. (İsteğe bağlı) Doğrulama kuralınızı depolamak için ayrı bir Sınıf kitaplığı projesi oluşturun.

    > [!IMPORTANT]
    > Sınıfını, testlerinizi içinde olduğu projede oluşturabilirsiniz. Ancak, kuralı yeniden kullanmak için kuralınızı depolamak üzere ayrı bir Sınıf kitaplığı projesi oluşturmanız daha iyi olur. Ayrı bir proje sanız, bu yordamda isteğe bağlı adımları tamamlamanız gerekir.

3. (İsteğe bağlı) Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework DLL'lerine bir başvuru ekleyin.

4. sınıfından türeten bir sınıf <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> oluşturun. ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> üyelerini <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*> uygulama.

5. (İsteğe bağlı) Yeni Sınıf kitaplığı projesini derleme.

6. (İsteğe bağlı) Test Project, özel doğrulama kuralını içeren Sınıf kitaplığı projesine bir başvuru ekleyin.

7. Test Project' içinde bir web performans testi **Web Performans Testi Düzenleyicisi.**

8. Özel doğrulama kuralını bir web performans testi isteğine eklemek için bir isteke sağ tıklayın ve Doğrulama Kuralı **Ekle'yi seçin.**

     Doğrulama **Kuralı Ekle** iletişim kutusu görüntülenir. Özel doğrulama kuralınızı Önceden tanımlanmış **doğrulama kurallarıyla** birlikte Kural seçin listesinde görünür. Özel doğrulama kuralınızı ve ardından Tamam'ı **seçin.**

9. Web performans testini çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod, özel doğrulama kuralının uygulamasını gösterir. Bu doğrulama kuralı, önceden tanımlanmış Gerekli Etiket doğrulama kuralının davranışını taklit ediyor. Kendi özel doğrulama kurallarınız için başlangıç noktası olarak bu örneği kullanın.

> [!WARNING]
> Özel doğrulayıcı için kodda genel özellikler null değerlere sahip olamaz.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Web performans testi için özel bir ayıklama kuralı kodlama](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
