---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118de9ec05bcd5c56376376619bea0c5148d36ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594194"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Visual Basic kod dosyaları için IntelliSense

Visual Basic kaynak kodu düzenleyicisi aşağıdaki IntelliSense özelliklerini sunar:

## <a name="syntax-tips"></a>Sözdizimi ipuçları

Sözdizimi ipuçları, yazdığınız deyimin sözdizimini görüntüler. Bu, [Bildirin](/dotnet/visual-basic/language-reference/statements/declare-statement)gibi ifadeler için yararlıdır.

## <a name="automatic-completion"></a>Otomatik tamamlama

- Çeşitli anahtar kelimelerde tamamlama

     Örneğin, bir boşluk `goto` ve yazarsanız, IntelliSense açılan menüde tanımlı etiketlerin listesini görüntüler. Desteklenen diğer anahtar `Exit` `Implements`kelimeler `Option`şunlardır: , , , ve `Declare`.

- Tamamlanma `Enum` ve`Boolean`

    Bir eksede numaralandırma nın bir üyesine atıfta bulunulduğunda, IntelliSense üye listesi `Enum`görüntüler. Bir deyim , `Boolean`IntelliSense gerçek-yanlış açılır menü görüntüler anlamına gelecektir.

Tamamlama, **Visual Basic** klasöründeki **Genel** özellik sayfasından Otomatik **liste üyelerini** seçerek varsayılan olarak kapatılabilir.

Liste Üyeleri, Tam Word veya **Alt**+**Sağ Ok'u**çağırarak el ile tamamlamayı çağırabilirsiniz. Daha fazla bilgi için Bkz. [IntelliSense'i kullan.](../ide/using-intellisense.md)

## <a name="intellisense-in-zone"></a>Bölgede IntelliSense

IntelliSense in Zone, uygulamaları dağıtması [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gereken ve kısmi güven ayarlarıyla sınırlandırılmış Visual Basic geliştiricilere yardımcı olur. Bu özellik:

- Uygulamanın çalışacağı izinleri seçmenize olanak tanır.

- Seçilen Bölge'deki API'leri Liste Üyeleri'nde kullanılabilir olarak görüntüleyin ve ek izinler gerektiren API'leri kullanılamaz olarak görüntüleyin.

Daha fazla bilgi [için ClickOnce uygulamaları için Kod erişim güvenliğine](../deployment/code-access-security-for-clickonce-applications.md)bakın.

## <a name="filtered-completion-lists"></a>Filtreuygulanmış tamamlama listeleri

Visual Basic'te, IntelliSense tamamlama listelerinde listelerin en altında bulunan iki sekme denetimi bulunur. Varsayılan olarak seçilen **Ortak** sekmesi, yazdığınız bildirimi tamamlamak için en sık kullanılan öğeleri görüntüler. **Tümü** sekmesi, **Ortak** sekmesinde bulunanlar da dahil olmak üzere otomatik tamamlama için kullanılabilen tüm öğeleri görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
