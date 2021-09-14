---
title: IIS Özellik Doğrulama Ayarlar | Microsoft Docs
description: IIS yönetim aracını kullanarak bir web uygulaması için ayar istediğiniz IIS özellik ayarlarını doğrulamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9742fb9ba7b7960dd3a82b2fe65af6a4e9bd7270
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725413"
---
# <a name="how-to-verify-iis-property-settings"></a>Nasıl Yapılır: IIS Özellik Ayarlarını Doğrulama

IIS yönetim aracını kullanarak bir Web uygulamasının özelliklerini ayarlayabilirsiniz. Uygulamanın çalışması için bu özelliklerin doğru şekilde ayarlanmış olması gerektiğinden, bu ayarların doğru olması genellikle sorun gidermede gerekli bir adımdır.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="to-check-iis-settings-for-the-web-application"></a>Web uygulamasının IIS ayarlarını kontrol etmek için

1. Yönetimsel **Araçlar penceresini** açın: Başlat menüsünde **Programlar'ın** üzerine **gelin** ve ardından Yönetimsel **Araçlar'a tıklayın.** **Yönetimsel** Araçlar Programlar menüsünde **görünmüyorsa,** yönetim menüsünden **Denetim Masası.**

   - 2000'Windows' **seçin** ve İnternet Hizmetleri Yöneticisi.

   - Xp Windows'de,'yi **Internet Information Services.**

   - Sunucu Windows 2003'te, Sunucuyu **Yönet'e çift tıklayın.**

        Sunucuyu **Yönet** penceresi açılır. Uygulama **Sunucusu altında Bu** uygulama sunucusunu **yönet'e tıklayın.**

        Uygulama **Sunucusu** penceresi açılır. Sol **bölmede Internet Information Services (IIS) Yöneticisi** düğümünü açın.

2. İletişim kutusunda makinenizin ağaç denetim düğümüne tıklayın. Web **Siteleri düğümüne** tıklayın ve Web uygulamasının düğümünü seçin. Bu bir Web sitesi düğümü ve bu nedenle Varsayılan Web Sitesi düğümünün bir kardesi ya da var olan **bir Web** sitesi düğümünün altındaki bir sanal dizin düğümü olur.

3. Web uygulamasına sağ tıklayın ve kısayol menüsünde Özellikler'e **tıklayın.**

4. Web uygulaması için güvenlik ayarlarını doğrulayın:

   1. Web uygulaması Özellikleri **penceresinde** Dizin Güvenliği **sekmesine ve Ardından** Düzenle'ye **tıklayın.**

   2. Kimlik Doğrulama **Yöntemleri iletişim kutusunda,** anonim **erişimi** etkinleştir ve tümleşik Windows **kimlik** doğrulamasını etkinleştir'i seçin.

   3. Kimlik **Doğrulama** Yöntemleri iletişim **kutusunu kapatmak için Tamam'a** tıklayın.

5. AtL Server uygulaması için DEBUG fiilinin ISAPI uzantınız ile ilişkili olduğunu doğrulayın. Daha fazla bilgi için, [bkz. How to: Associate DEBUG Fiil with Extension](/previous-versions/ms165022(v=vs.100)).

6. Bir uygulama için, uygulamanın sanal klasöründe Internet Information Services [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **(IIS) Yöneticisi**, İnternet Hizmetleri Yöneticisi  veya Internet Information Services. 

   1. Web uygulaması **Özellikleri penceresinde,**  uygulama bir sanal dizinde ise Dizin sekmesini  veya uygulama bir Web sitesinde ise Giriş Dizini sekmesini seçin.

   2. Yerel yol'daki **adın, uygulamanın** gerçekten dağıtıldığından emin olun.

   3. Uygulama **Ayarlar** altında, uygulamayı içeren kök dizinin adını yazın.

   4. Özellikler **iletişim** kutusunu kapatmak için **Tamam'a** tıklayın.

7. Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama için  ASP.NET sekmesine tıklayın ve doğru sürümünün belirtilmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] olduğunu doğrulayın.

8. Özellikler **iletişim** kutusunu kapatmak için **Tamam'a** tıklayın.

9. Internet Information Services  **(IIS) Yöneticisi**, İnternet Hizmetleri Yöneticisi veya **Internet Information Services** iletişim kutusunu kapatmak için **Tamam'a** tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorun giderme](../debugger/debugging-web-applications-troubleshooting.md)