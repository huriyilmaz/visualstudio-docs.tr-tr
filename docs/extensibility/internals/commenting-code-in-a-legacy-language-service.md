---
title: Eski Dil Hizmeti hizmetlerinde koda açıklama | Microsoft Docs
description: Eski dil hizmetlerinde kod açıklaması desteği sağlayan yönetilen paket çerçevesi (MPF) sınıfları hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d01cb64696e4f440ad0c92125dab0411c722371f2d86f478c5553f0f02f9e013
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321224"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Eski dil hizmetlerinde açıklama kodu
Programlama dilleri genellikle koda not ek açıklama veya açıklama sağlamak için bir kaynak sağlar. Açıklama, kod hakkında ek bilgi sağlayan ancak derleme veya yorumlama sırasında yoksayılan bir metin bölümüdir.

 Yönetilen paket çerçevesi (MPF) sınıfları, seçilen metne açıklama ekleme ve açıklamalarını geri alma desteği sağlar.

## <a name="comment-styles"></a>Açıklama stilleri
Açıklamanın iki genel stili vardır:

1. Açıklamanın tek bir satırda olduğu satır yorumları.

2. Açıklamanın birden çok satır içermesi için açıklama bloğu.

Satır açıklamalarının genellikle bir başlangıç karakteri (veya karakteri) olurken, blok açıklamalarının hem başlangıç hem de bitiş karakterleri olur. Örneğin, C# içinde bir satır açıklaması ile başlar ve blok açıklaması ile `//` başlar `/*` ve ile `*/` biter.

Kullanıcı Gelişmiş Düzenle **menüsünden Açıklama** Seçimi komutunu  >   seçerken, komut sınıfındaki <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> yöntemine <xref:Microsoft.VisualStudio.Package.Source> yönlendirildi. Kullanıcı, **Uncomment Selection komutunu seçerek** yöntemine <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> yönlendirildi.

## <a name="support-code-comments"></a>Kod açıklamalarını destekleme
 Dil hizmeti destek kodu açıklamalarınızı, 'nin adlandırılmış `EnableCommenting` parametresiyle <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> sebilirsiniz. Bu, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> sınıfının özelliğini <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ayarlar. Dil hizmeti özelliklerini ayarlama hakkında daha fazla bilgi için [bkz. Eski dil hizmetini kaydetme.](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Ayrıca dilinizin açıklama <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> karakterleriyle bir <xref:Microsoft.VisualStudio.Package.CommentInfo> yapıyı geri dönmek için yöntemini geçersiz kılmanız gerekir. C#-style satır açıklaması karakterleri varsayılandır.

### <a name="example"></a>Örnek
 Yönteminin örnek bir uygulaması aşağıdaki <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> gibidir.

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
- [Eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)
