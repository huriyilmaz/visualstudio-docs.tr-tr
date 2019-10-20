---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa21939375956024a0ca16cadd99160d142a1d5d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647266"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Visual Basic kod dosyaları için IntelliSense

Visual Basic kaynak kodu Düzenleyicisi aşağıdaki IntelliSense özelliklerini sunar:

## <a name="syntax-tips"></a>Söz dizimi ipuçları

Söz dizimi ipuçları, yazmakta olduğunuz deyimin sözdizimini görüntüler. Bu, [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)gibi deyimler için kullanışlıdır.

## <a name="automatic-completion"></a>Otomatik tamamlama

- Çeşitli anahtar sözcüklerde tamamlama

     Örneğin, `goto` ve bir boşluk yazarsanız, IntelliSense açılan menüdeki tanımlı etiketlerin bir listesini görüntüler. Desteklenen diğer anahtar sözcükler `Exit`, `Implements`, `Option` ve `Declare` içerir.

- @No__t_0 ve `Boolean` tamamlama

    Bir ifade bir numaralandırmanın üyesine başvuracaktır, IntelliSense `Enum` üyelerinin bir listesini görüntüler. Bir deyimin `Boolean` başvurması durumunda IntelliSense, true-false açılan menüsünü görüntüler.

Tamamlama, **Visual Basic** klasöründeki **genel** özellik sayfasından **otomatik liste üyelerinin** seçimini kaldırarak varsayılan olarak devre dışı bırakabilirsiniz.

Liste üyelerini çağırarak tamamlamayı el ile çağırabilirsiniz, kelime veya **Alt** +**sağ oku**. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Bölgedeki IntelliSense

Bölgedeki IntelliSense, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] üzerinden uygulama dağıtması gereken ve kısmi güven ayarları ile sınırlandırmaları gereken geliştiricilerin Visual Basic yardımcı olur. Bu özellik:

- Uygulamanın çalışacağı izinleri seçmenizi sağlar.

- Seçili bölgede API 'Leri liste üyelerinde kullanılabilir olarak görüntüle ve kullanılamaz olarak ek izinler gerektiren API 'Leri görüntüle.

Daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrelenmiş tamamlanma listeleri

Visual Basic, IntelliSense tamamlanma listelerinde, listelerin en altında bulunan iki sekme denetimi vardır. Varsayılan olarak seçilen **ortak** sekme, yazmakta olduğunuz ifadeyi tamamlayacak en sık kullanılan öğeleri görüntüler. **Tümü** sekmesi, **genel** sekmesinde olanlar da dahil olmak üzere, otomatik tamamlama için kullanılabilir olan tüm öğeleri görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)