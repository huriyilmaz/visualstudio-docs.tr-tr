---
title: Eski Dil Hizmetinde Yorum Kodu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709433"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Eski bir dil hizmetinde açıklama kodu
Programlama dilleri genellikle koda açıklama ek etmek veya yorum yapmak için bir araç sağlar. Açıklama, metnin kod hakkında ek bilgi sağlayan, ancak derleme veya yorumlama sırasında yoksayılabilen bir bölümüdür.

 Yönetilen paket çerçevesi (MPF) sınıfları, seçili metnin yorumlanması ve yorumlanması için destek sağlar.

## <a name="comment-styles"></a>Yorum stilleri
Yorum iki genel stilleri vardır:

1. Yorumun tek bir satırda olduğu satır açıklamaları.

2. Açıklamanın birden çok satır içerebileceği yorumları engelleyin.

Satır açıklamaları genellikle bir başlangıç karakterine (veya karaktere) sahipken, blok açıklamaları nın hem başlangıç hem de bitiş karakterleri vardır. Örneğin, C#'da bir satır `//`yorumu ile başlar ve `/*` bir `*/`blok yorumu ile başlar ve .

Kullanıcı**Gelişmiş** **Gelişmiş'i Edit** > menüsünden **Yorum Seçimi** komutunu seçtiğinde, komut <xref:Microsoft.VisualStudio.Package.Source> sınıftaki <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> yönteme yönlendirilir. Kullanıcı **YorumSuz Seçim**komutunu seçtiğinde, komut <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> yönteme yönlendirilir.

## <a name="support-code-comments"></a>Destek kodu açıklamaları
 Dil hizmeti destek kodu `EnableCommenting` yorumlarınızı, adı geçen parametre <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> ile elde edebilirsiniz. Bu sınıfın <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> özelliğini <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ayarlar. Dil hizmeti özelliklerini ayarlama hakkında daha fazla bilgi için [bkz.](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Ayrıca, diliniz <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> için yorum <xref:Microsoft.VisualStudio.Package.CommentInfo> karakterleri içeren bir yapıyı döndürmek için yöntemi geçersiz kılmanız gerekir. C#tarzı satır yorumu karakterleri varsayılandır.

### <a name="example"></a>Örnek
 Burada yöntemin <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> bir örnek uygulamasıdır.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
- [Eski bir dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)
