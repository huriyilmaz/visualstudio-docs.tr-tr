---
title: Eski dil hizmetlerindeki özel belge özellikleri
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c38ad28456ab8b9bccf29d2249307b718a5767b
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036840"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Eski dil hizmetindeki özel belge özellikleri
Belge özellikleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Özellikler** penceresinde gösterilebilir. Programlama dillerinin genellikle ayrı kaynak dosyalarla ilişkili özellikleri yoktur. Ancak, XML kodlama, şema ve stil sayfasını etkileyen belge özelliklerini destekler.

## <a name="discussion"></a>Tartışma
 Diliniz özel belge özelliklerine ihtiyaç duyuyorsa, sınıftan bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.DocumentProperties> ve türetilmiş sınıfınıza gerekli özellikleri uygulamanız gerekir.

 Ayrıca, belge özellikleri genellikle kaynak dosyanın kendisinde depolanır. Bu, dil hizmetinin Özellik bilgilerini **Özellikler** penceresinde görüntülenecek şekilde kaynak dosyadan ayrıştırması ve **Özellikler** penceresindeki belge özelliklerinde değişiklik yapıldığında kaynak dosyanın güncelleştirilmesini gerektirir.

## <a name="customize-the-documentproperties-class"></a>DocumentProperties sınıfını özelleştirme
 Özel belge özelliklerini desteklemek için, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.DocumentProperties> ve ihtiyacınız olan kadar çok özellik eklemeniz gerekir. Ayrıca, **Özellikler** penceresi görünümü ' nde bunları düzenlemek için Kullanıcı öznitelikleri sağlamanız gerekir. Bir özelliğin yalnızca bir erişimcisi varsa `get` , **Özellikler** penceresinde salt okuma olarak gösterilir. Bir özellikte hem hem de `get` `set` erişimcileri varsa, özellik **Özellikler** penceresinde de güncelleştirilemeyebilir.

### <a name="example"></a>Örnek
 Aşağıda, <xref:Microsoft.VisualStudio.Package.DocumentProperties> iki özelliği gösteren ve ' den türetilmiş bir örnek sınıf `Filename` verilmiştir `Description` . Bir özellik güncelleştirildiği zaman, <xref:Microsoft.VisualStudio.Package.LanguageService> kaynak dosyaya özelliği yazmak için sınıfında özel bir yöntem çağırılır.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Özel DocumentProperties sınıfının örneğini oluşturma
 Özel belge özellikleri sınıfınızı oluşturmak için, sınıfınızın <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> tek bir örneğini döndürmek üzere sınıfının sürümündeki yöntemini geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.DocumentProperties> .

### <a name="example"></a>Örnek

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Kaynak dosyadaki Özellikler
 Belge özellikleri genellikle kaynak dosyaya özel olduğundan, değerler kaynak dosyasında depolanır. Bu özellikleri tanımlamak için dil ayrıştırıcısında veya tarayıcıda destek gerekir. Örneğin, bir XML belgesinin özellikleri kök düğümünde depolanır. Kök düğümdeki değerler, **Özellikler** penceresi değerleri değiştirildiğinde değiştirilir ve kök düğüm düzenleyicide güncelleştirilir.

### <a name="example"></a>Örnek
 Bu örnek, aşağıdaki `Filename` `Description` gibi özel bir yorum başlığına gömülü olan kaynak dosyanın ilk iki satırını ve özelliklerini depolar:

```
//!Filename = file.testext
//!Description = A sample file
```

 Bu örnek, belge özelliklerini almak ve kaynak dosyanın ilk iki satırının yanı sıra Kullanıcı kaynak dosyayı doğrudan değiştirirse özelliklerin nasıl güncelleştirileceğini gösteren iki yöntemi gösterir. `SetPropertyValue`Burada gösterilen örnekteki yöntemi, `TestDocumentProperties` *DocumentProperties sınıfını özelleştirme* bölümünde gösterildiği gibi sınıfından çağrılan bir yöntemdir.

 Bu örnek, ilk iki satırlardaki belirteçlerin türünü belirleyebilmek için tarayıcıyı kullanır. Bu örnek yalnızca tanım amaçlıdır. Bu duruma yönelik daha yaygın bir yaklaşım, kaynak dosyayı ağacın her bir düğümünün belirli bir belirteç hakkında bilgi içerdiği bir ayrıştırma ağacı olarak ayrıştırmaktır. Kök düğüm belge özelliklerini içerir.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
