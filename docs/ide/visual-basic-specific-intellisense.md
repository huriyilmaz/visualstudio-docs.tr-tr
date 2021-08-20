---
title: Visual Basic IntelliSense
description: Kaynak kodu düzenleyicisi tarafından sunulan IntelliSense özelliklerini Visual Basic öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 44b6e8eb5b44089f0aa87c579ea98f6be947bdb9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150813"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Kod dosyalarını Visual Basic IntelliSense

Kaynak Visual Basic düzenleyicisi aşağıdaki IntelliSense özelliklerini sunar:

## <a name="syntax-tips"></a>Söz dizimi ipuçları

Söz dizimi ipuçları yazdığınız deyimin söz dizimlerini görüntüler. Bu, Declare gibi deyimler için [kullanışlıdır.](/dotnet/visual-basic/language-reference/statements/declare-statement)

## <a name="automatic-completion"></a>Otomatik tamamlama

- Çeşitli anahtar sözcüklerde tamamlama

     Örneğin, bir boşluk ve `goto` yazmanız durumunda IntelliSense, açılan menüde tanımlı etiketlerin listesini görüntüler. Desteklenen diğer anahtar sözcükler : `Exit` , `Implements` , ve `Option` `Declare` .

- ve üzerinde `Enum` tamamlama `Boolean`

    Bir deyim, bir liste üyesine başvuracaksa, IntelliSense' in üyelerinin listesini `Enum` görüntüler. bir deyimine başvuracaksa, `Boolean` IntelliSense true-false açılan menüsünü görüntüler.

Tamamlama, Visual Basic klasöründeki Genel özellik  sayfasından Otomatik  liste üyeleri seçimini **kaldırarak varsayılan olarak Visual Basic** kapatabilirsiniz.

List Members, Complete Word veya **Alt** Right Arrow çağrılarını kullanarak tamamlamayı el + **ile çağırabilirsiniz.** Daha fazla bilgi için [bkz. IntelliSense kullanma.](../ide/using-intellisense.md)

## <a name="intellisense-in-zone"></a>Bölgede IntelliSense

Zone'da IntelliSense, Visual Basic dağıtması gereken ve kısmi güven ayarlarıyla kısıtlanmış olan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geliştiricilere yardımcı olur. Bu özellik:

- Uygulamanın çalıştıracakları izinleri seçmenizi sağlar.

- Seçilen Bölgede API'leri Liste Üyeleri'nde kullanılabilir olarak ve ek izinler gerektiren API'leri kullanılamaz olarak görüntüler.

Daha fazla bilgi için [bkz. Uygulama uygulamaları için ClickOnce güvenliği.](../deployment/code-access-security-for-clickonce-applications.md)

## <a name="filtered-completion-lists"></a>Filtrelenmiş tamamlama listeleri

Bu Visual Basic IntelliSense tamamlama listelerinde, listelerin alt kısmında iki sekme denetimi bulunur. Varsayılan **olarak** seçilen Ortak sekmesi, yazmakta olduğunuz deyimi tamamlamak için en sık kullanılan öğeleri görüntüler. Tüm **sekmesi,** Ortak sekmesinde de bulunanlar da dahil olmak üzere otomatik tamamlama için kullanılabilen tüm **öğeleri** görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
