---
title: Gelişmiş güvenlik ayarları Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651745"
---
# <a name="advanced-security-settings-dialog-box"></a>Gelişmiş Güvenlik Ayarları İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusu, bölgede hata ayıklama ile ilgili güvenlik ayarlarını belirtmenize olanak tanır.

 Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **güvenlik** sekmesine tıklayın. **Güvenlik** sayfasında, **ClickOnce güvenlik ayarlarını etkinleştir**' i seçin, **Bu kısmi güven uygulaması**' na tıklayın ve ardından **Gelişmiş**' e tıklayın.

## <a name="uielement-list"></a>UIElement Listesi
 **Bu uygulamada seçili izin kümesiyle hata ayıkla** Bu onay kutusunu seçerseniz, **güvenlik** sayfasında seçilen izin kümesi hata ayıklama sırasında kullanılır. Varsayılan olarak, bu seçenek seçilidir.

 Bir güvenlik bölgesindeki hata ayıklamanın çalışması için, bu seçeneğin etkinleştirilmesi gerekir; Ayrıca, **Visual Studio barındırma Işlemini etkinleştir** seçeneği ( **Proje Tasarımcısı**'nın **hata ayıklama** sayfasında bulunur) etkinleştirilmelidir.

 WPF Web tarayıcısı uygulama projeleri için, **Bu uygulamanın seçilen izin kümesi Ile hata ayıkla** seçeneği işaretlendi ve devre dışı bırakıldı.

 **Uygulamanın kaynak sitesine erişimini verme** Bu onay kutusunu seçerseniz, uygulama yayımlanan Web sitesine veya sunucu paylaşımında erişebilir. Varsayılan olarak, bu seçenek seçilidir.

 **Bu uygulamada AŞAĞıDAKI URL 'den indirilmiş gibi hata ayıkla** Uygulamanın **Yayımla** sayfasında BELIRTTIĞINIZ **yükleme URL** 'sine karşılık gelen Web sitesine veya sunucu paylaşımının erişimine izin vermeniz gerekiyorsa, URL 'yi buraya yazın. Bu seçenek yalnızca **uygulamanın kaynak sitesine erişimi** olduğunda kullanılabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenlik Sayfası, Proje Tasarımcısı](../../ide/reference/security-page-project-designer.md)
