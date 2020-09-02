---
title: Eski dil hizmetindeki oto penceresi için destek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 01d2046d7693b23865555abb06962dead4a435ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157589"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu **pencere,** hata ayıklamakta olan program duraklatıldığında (kesme noktası ya da bir özel durum nedeniyle) kapsamdaki değişkenler ve parametreler gibi ifadeleri görüntüler. İfadeler, yerel kapsamda değiştirilmiş değişkenleri, yerel veya genel ve parametreleri içerebilir. Ayrıca **, bir** sınıf, yapı veya başka bir türün örneklemeleri de içerebilir. Bir ifade değerlendirici 'nin değerlendirebileceği her türlü şey, **oto** penceresinde görüntülenebilir.  
  
 Yönetilen paket çerçevesi (MPF), **oto** penceresi için doğrudan destek sağlamaz. Ancak, yöntemini geçersiz kılarsınız <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> , **oto** penceresinde sunulacak ifadelerin bir listesini döndürebilirsiniz.  
  
## <a name="implementing-support-for-the-autos-window"></a>Oto penceresi için destek uygulama  
 **Oto** penceresini desteklemek için yapmanız gereken tek şey, <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfına uygulamaktır. Uygulamanız kaynak dosyasında bir konum verilmeye karar vermelidir, hangi ifadeler **oto** penceresinde görünmelidir. Yöntemi, her bir dizenin tek bir ifadeyi temsil ettiği dizelerin listesini döndürür. Dönüş değeri, <xref:Microsoft.VisualStudio.VSConstants.S_OK> listenin ifadeler içerdiğini, ancak <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> gösterilecek hiçbir ifade olmadığını gösterir.  
  
 Döndürülen gerçek ifadeler, koddaki bu konumda görünen değişkenlerin veya parametrelerin adlarıdır. Bu adlar, daha sonra **oto** penceresinde görüntülenen değerleri ve türleri almak için ifade değerlendirici 'e geçirilir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırma nedenini kullanarak yöntemden bir ifade listesi alan bir yönteminin bir uygulamasını gösterir <xref:Microsoft.VisualStudio.Package.ParseReason> . İfadelerin her biri, arabirimini uygulayan bir olarak sarmalanır `TestVsEnumBSTR` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> .  
  
 `GetAutoExpressionsCount`Ve `GetAutoExpression` yöntemlerinin nesne üzerinde özel yöntemler olduğunu `TestAuthoringSink` ve bu örneği desteklemek için eklendiğini unutmayın. Bu, ayrıştırıcının nesneye eklenen ifadelere `TestAuthoringSink` ( <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> yöntemini çağırarak) ayrıştırıcı dışında erişilebilen bir yolu temsil eder.  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```
