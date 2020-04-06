---
title: Eski Dil Hizmetinde Özel Belge Özellikleri | Microsoft Dokümanlar
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
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708964"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Eski bir dil hizmetinde özel belge özellikleri
Belge özellikleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Özellikler** penceresinde görüntülenebilir. Programlama dilleri genellikle tek tek kaynak dosyaları ile ilişkili özelliklere sahip değildir. Ancak, XML kodlama, şema ve stil sayfasını etkileyen belge özelliklerini destekler.

## <a name="discussion"></a>Tartışma
 Diliniz özel belge özelliklerine ihtiyaç duyarsa, <xref:Microsoft.VisualStudio.Package.DocumentProperties> sınıftan bir sınıf türetmeniz ve türemiş sınıfınızda gerekli özellikleri uygulamanız gerekir.

 Ayrıca, belge özellikleri genellikle kaynak dosyanın kendisinde depolanır. Bu, dil hizmetinin kaynak dosyadaki özellik bilgilerini **Özellikler** penceresinde görüntülemek üzere ayrıştırmasını ve **Özellikler** penceresindeki belge özelliklerinde değişiklik yapıldığında kaynak dosyayı güncelleştirmesini gerektirir.

## <a name="customize-the-documentproperties-class"></a>DocumentProperties sınıfını özelleştirme
 Özel belge özelliklerini desteklemek <xref:Microsoft.VisualStudio.Package.DocumentProperties> için, sınıftan bir sınıf türetmeniz ve istediğiniz kadar özellik eklemeniz gerekir. **Ayrıca, Özellikler** penceresinde bunları düzenlemek için kullanıcı öznitelikleri sağlamanız gerekir. Bir özelliğin yalnızca `get` bir erişimcisi varsa, **Özellikler** penceresinde salt okunur olarak gösterilir. Bir özellikte `get` hem `set` de erişime sahipse, **özellik Özellikler** penceresinde de güncelleştirilebilir.

### <a name="example"></a>Örnek
 Burada, iki özelliği <xref:Microsoft.VisualStudio.Package.DocumentProperties>gösteren bir örnek `Filename` `Description`sınıf ve . Bir özellik güncelleştirildiğinde, özelliği <xref:Microsoft.VisualStudio.Package.LanguageService> kaynak dosyaya yazmak için sınıftaki özel bir yöntem çağrılır.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Özel DocumentProperties sınıfını anında aygıt
 Özel belge özellikleri sınıfınızı anında yapmak için, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> sınıfınızın tek bir <xref:Microsoft.VisualStudio.Package.LanguageService> örneğini döndürmek için <xref:Microsoft.VisualStudio.Package.DocumentProperties> sınıfın sürümündeki yöntemi geçersiz kılmanız gerekir.

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

## <a name="properties-in-the-source-file"></a>Kaynak dosyadaki özellikler
 Belge özellikleri genellikle kaynak dosyaya özgü olduğundan, değerler kaynak dosyanın kendisinde depolanır. Bu, bu özellikleri tanımlamak için dil parser veya tarayıcı desteği gerektirir. Örneğin, bir XML belgenin özellikleri kök düğümünde depolanır. **Özellikler** penceresi değerleri değiştirildiğinde kök düğümündeki değerler değiştirilir ve kök düğüm düzenleyicide güncelleştirilir.

### <a name="example"></a>Örnek
 Bu örnek, `Filename` özellikleri `Description` depolar ve kaynak dosyanın ilk iki satırında, özel bir yorum üstbilgisinde katıştırılmış, aşağıdaki gibi:

```
//!Filename = file.testext
//!Description = A sample file
```

 Bu örnek, kaynak dosyanın ilk iki satırından belge özelliklerini almak ve ayarlamak için gereken iki yöntemi ve kullanıcı kaynak dosyayı doğrudan değiştirirse özelliklerin nasıl güncelleştirilebildiğini gösterir. Burada `SetPropertyValue` gösterilen örnekteki yöntem, `TestDocumentProperties` *DocumentProperties sınıfını Özelleştirme* bölümünde gösterildiği gibi sınıftan çağrılan yöntemle aynıdır.

 Bu örnek, ilk iki satırdaki belirteçlerin türünü belirlemek için tarayıcıyı kullanır. Bu örnek yalnızca açıklayıcı amaçlar içindir. Bu duruma daha tipik bir yaklaşım, kaynak dosyayı, ağacın her düğümünün belirli bir belirteç hakkında bilgi içerdiği ayrıştırıcı ağaç olarak adlandırılan dosyaya ayrıştırmaktır. Kök düğüm belge özelliklerini içerir.

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
