---
title: Eşitlenmiş Ayarlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6459b6f65fd1e29fbadb01f6aa2fc51520b726b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646821"
---
# <a name="synchronized-settings-in-visual-studio"></a>Visual Studio'da Eşitlenmiş Ayarlar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aynı kişiselleştirme hesabını birden çok bilgisayarda Visual Studio 'da oturum açmak için kullandığınızda, varsayılan olarak ayarlarınız tüm bilgisayarlarda eşitlenir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar
 Varsayılan olarak, aşağıdaki ayarlar eşitlenir.

- Geliştirme ayarları (Visual Studio 'Yu ilk kez çalıştırdığınızda bir ayar kümesi seçmeniz gerekir, ancak seçimi dilediğiniz zaman değiştirebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)

- **Araçlar &#124; seçenekler** sayfalarında aşağıdaki seçenekler:

  - **Tema** ve menü çubuğu büyük/küçük harf ayarları, **ortam**, **genel** Seçenekler sayfası

  - **Ortam**, **yazı tipleri ve renkler** seçenekleri sayfasındaki tüm ayarlar

  - **Ortam**, **klavye** seçenekleri sayfasındaki tüm klavye kısayolları

  - **Ortamdaki, sekmelerin ve Windows** seçenekleri sayfasındaki tüm ayarlar

  - **Ortamdaki**tüm ayarlar, **Başlangıç** seçenekleri sayfası

  - **Metin düzenleyici** seçenekleri sayfalarındaki tüm ayarlar

- XAML Tasarımcısı seçenekleri sayfalarındaki tüm ayarlar

- Kullanıcı tanımlı komut diğer adları. Komut diğer adlarının nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

- Pencere içindeki kullanıcı tanımlı pencere düzenleri **pencere &#124; düzenlerini yönetme** sayfası

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Belirli bir bilgisayar için eşitlenmiş ayarları kapatma
 Visual Studio için eşitlenmiş ayarlar varsayılan olarak açıktır. Bir bilgisayardaki eşitlenmiş ayarları, **Araçlar &#124; Seçenekler &#124; &#124; ortam eşitlenmiş ayarlar** sayfasına gidip onay kutusunun işaretini kaldırarak devre dışı bırakabilirsiniz.  Örneğin, A bilgisayarında Visual Studio 'nun ayarlarını eşitlememeye karar verirseniz, A bilgisayarında yapılan herhangi bir ayar değişikliği, B veya bilgisayar C 'de görünmez. B ve C bilgisayarı, bilgisayar A 'ya değil birbirleriyle eşitlemeye devam edecektir.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ailesi ürünleri ve sürümleri arasında ayarları eşitleme
 Ayarlar, Express ve Community sürümleri dahil olmak üzere herhangi bir Visual Studio 2015 sürümü arasında eşitlenebilir. Ayrıca ayarlar, Blend gibi Visual Studio ailesi ürünleri arasında da eşitlenir. Ancak, bu aile ürünlerinin her biri Visual Studio ile paylaşılmayan kendi ayarlarına sahip olabilir. Örneğin, A bilgisayarındaki Blend 'e özgü ayarlar, bilgisayar B 'de Blend ile paylaşılır, ancak A veya B bilgisayarında Visual Studio ile birlikte kullanılamaz.

> [!WARNING]
> Ayarlar Visual Studio 2013 ve Visual Studio 2015 arasında eşitlenmez. Visual Studio 2015 ' i ilk açışınızda Visual Studio 2013 ayarları geçirilir, ancak bundan sonra Visual Studio 2013 geri geçirilemez.

## <a name="see-also"></a>Ayrıca Bkz.
 [IDE’yi Kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
