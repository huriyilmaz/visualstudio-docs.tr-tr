---
title: Eski Dil Hizmetinde Otomatik Pencere Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704892"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek
Otomatik Ler penceresi, program debugged duraklatıldızaman kapsamda olan **değişkenler** ve parametreler gibi ifadeler görüntüler (bir kesme noktası veya özel durum nedeniyle). İfadeler, yerel veya genel değişkenler ve yerel kapsamda değiştirilen parametreleri içerebilir. **Otomatik Ler** penceresi, bir sınıfın, yapının veya başka bir türün anlık görüntülerini de içerebilir. Bir ifade değerlendiricinin değerlendirebileceği her şey **Otomatik Ler** penceresinde gösterilebilir.

 Yönetilen paket çerçevesi (MPF), **Otomatik ler** penceresi için doğrudan destek sağlamaz. Ancak, <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> yöntemi geçersiz kılarsanız, **Otomatik Ler** penceresinde sunulacak ifadelerin listesini döndürebilirsiniz.

## <a name="implementing-support-for-the-autos-window"></a>Otomatik Pencere için Destek Uygulama
 **Otomatik sistem** penceresini desteklemek için tek yapmanız <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> gereken, <xref:Microsoft.VisualStudio.Package.LanguageService> yöntemin sınıfta uygulanmasıdır. Uygulamanız, kaynak dosyadaki bir konum göz önüne alındığında, **Otomatik Ler** penceresinde hangi ifadelerin görünmesi gerektiğine karar vermelidir. Yöntem, her dize tek bir ifadeyi temsil ettiği dizeleri bir listesini döndürür. Bir geri <xref:Microsoft.VisualStudio.VSConstants.S_OK> dönüş değeri, listenin ifadeleri <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> içerdiğini gösterirken, gösterilen ifadeler olmadığını gösterir.

 Döndürülen gerçek ifadeler, koddaki o konumda görünen değişkenlerin veya parametrelerin adlarıdır. Bu adlar, daha sonra **Otomatik Ler** penceresinde görüntülenen değerleri ve türleri elde etmek için ifade değerlendiriciye geçirilir.

### <a name="example"></a>Örnek
 Aşağıdaki örnekte, ayrışdırış nedenini <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason>kullanarak yöntemden ifadelerin listesini alan yöntemin bir uygulaması gösterilmektedir. İfadelerin her biri `TestVsEnumBSTR` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> arabirimi uygulayan bir şekilde sarılır.

 Ve `GetAutoExpressionsCount` `GetAutoExpression` yöntemlerin `TestAuthoringSink` nesneüzerinde özel yöntemler olduğunu ve bu örneği desteklemek için eklenmiştir unutmayın. Bunlar, `TestAuthoringSink` parçacı tarafından nesneye eklenen ifadelerin <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> (yöntemi çağırarak) ayrıştırıcının dışında erişilebildiği bir yolu temsil eder.

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
