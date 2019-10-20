---
title: Visual Basic özel IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c6895abd85a4394e4ddcaebcd6f09bc0a39936cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663026"
---
# <a name="visual-basic-specific-intellisense"></a>Visual Basic'e Özel IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic kaynak kodu Düzenleyicisi aşağıdaki IntelliSense özelliklerini sunar:

- Söz dizimi ipuçları

     Söz dizimi ipuçları, yazmakta olduğunuz deyimin sözdizimini görüntüler. Bu, [Declare](https://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1)gibi deyimler için kullanışlıdır.

## <a name="automatic-completion"></a>Otomatik tamamlama

- Çeşitli anahtar sözcüklerde tamamlama

   Örneğin, `goto` ve bir boşluk yazarsanız, IntelliSense açılan menüdeki tanımlı etiketlerin bir listesini görüntüler. Desteklenen diğer anahtar sözcükler `Exit`, `Implements`, `Option` ve `Declare` içerir.

- @No__t_0 ve `Boolean` tamamlama

   Bir ifade bir numaralandırmanın üyesine başvuracaktır, IntelliSense `Enum` üyelerinin bir listesini görüntüler. Bir deyimin `Boolean` başvurduğu zaman IntelliSense, true-false açılan menüsünü görüntüler.

  Tamamlama, **Visual Basic** klasöründeki **genel** özellik sayfasından **otomatik liste üyelerinin** seçimini kaldırarak varsayılan olarak devre dışı bırakabilirsiniz.

  Liste üyelerini, tamamla sözcüğünü veya ALT + sağ oku çağırarak tamamlamayı el ile çağırabilirsiniz. Daha fazla bilgi için bkz. [IntelliSense kullanma](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Bölgedeki IntelliSense
 Bölgedeki IntelliSense, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] üzerinden uygulama dağıtması gereken ve kısmi güven ayarları ile sınırlandırmaları gereken geliştiricilerin Visual Basic yardımcı olur. Bu özellik:

- Uygulamanın çalışacağı izinleri seçmenizi sağlar.

- Seçili bölgede API 'Leri liste üyelerinde kullanılabilir olarak görüntüle ve kullanılamaz olarak ek izinler gerektiren API 'Leri görüntüle.

  Daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense Kullanma](../ide/using-intellisense.md)
