---
title: Eski dil hizmetlerinde Otomatikler penceresini destekleme
description: Hata ayıklaması yapılan program duraklatılırken kapsamda olan ifadeleri görüntüleyen Otomatikler penceresi için desteğin nasıl uygulandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d91cad3e47ca664cfb1f41215da3197774e3840e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086592"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Eski dil hizmetlerinde Otomatikler penceresi desteği

**Otomatikler** penceresinde, hata ayıklarken program duraklatılırken (kesme noktası veya özel durum nedeniyle) kapsamda olan değişkenler ve parametreler gibi ifadeler görüntülenir. İfadeler değişkenler, yerel veya genel ve yerel kapsamda değiştirilmiş parametreleri içerebilir. **Otomatikler** penceresi bir sınıfın, yapının veya başka bir türün örneklerini de içerebilir. Bir ifade değerlendiricinin değerlendirebilecekleri her şey, Otomatikler **penceresinde gösterebilirsiniz.**

 Yönetilen paket çerçevesi (MPF), Otomatikler penceresi için doğrudan **destek sağlamaz.** Ancak, yöntemini geçersiz <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> kılarsanız, Otomatikler penceresinde sunulacak ifadelerin listesini **getirebilirsiniz.**

## <a name="implementing-support-for-the-autos-window"></a>Otomatikler penceresi için destek uygulama

 Otomatikler penceresini desteklemek için **tek gereken** sınıfında yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> uygulamaktır. Kaynak dosyada, otomatikler penceresinde hangi ifadelerin görünmesi gerektiğine  uygulamanız karar vermalıdır. yöntemi, her dizenin tek bir ifadeyi temsil ettiği dizelerin listesini döndürür. dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK> değeri, listede ifadelerin olduğunu, ise <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> gösterilen hiçbir ifade olmadığını gösterir.

 Döndürülen gerçek ifadeler, kodda bu konumda görünen değişkenlerin veya parametrelerin adlarıdır. Bu adlar, daha sonra Otomatikler penceresinde görüntülenen değerleri ve türleri almak için ifade **değerlendiricisine** geçir edilir.

### <a name="example"></a>Örnek
 Aşağıdaki örnek ayrıştırma nedenini kullanarak yönteminden ifade listesini alan <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminin uygulamasını <xref:Microsoft.VisualStudio.Package.ParseReason> gösterir. İfadelerin her biri arabirimi uygulayan `TestVsEnumBSTR` bir olarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> sarmalanmış.

 ve `GetAutoExpressionsCount` yöntemlerinin `GetAutoExpression` nesnede özel yöntemler olduğunu ve `TestAuthoringSink` bu örneği desteklemek için ekli olduğunu unutmayın. Ayrıştırıcı tarafından nesneye eklenen ifadelerin (yöntemi çağrılarak) ayrıştırıcının dışında erişilme yöntemini temsil `TestAuthoringSink` <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> eder.

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
