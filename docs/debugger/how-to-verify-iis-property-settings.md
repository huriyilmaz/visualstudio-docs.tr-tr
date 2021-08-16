---
title: ııs özelliğini doğrula Ayarlar | Microsoft Docs
description: IIS yönetim aracını kullanarak bir Web uygulaması için ayarladığınız IIS özellik ayarlarını doğrulama hakkında bilgi edinin.
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
ms.openlocfilehash: ad9b7d95e6700e7950d92282e86ca86d12d824a18f288acd10a3939b945bfb45
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453259"
---
# <a name="how-to-verify-iis-property-settings"></a>Nasıl Yapılır: IIS Özellik Ayarlarını Doğrulama

IIS yönetim aracını kullanarak bir Web uygulamasının özelliklerini ayarlayabilirsiniz. Uygulamanın çalışması için bu özelliklerin doğru ayarlanmış olması gerekir, bu nedenle bu ayarların doğrulanması genellikle sorun gidermede gerekli bir adımdır.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. ayarlarınızı değiştirmek için **araçlar** menüsünden **içeri aktar ve dışarı aktar Ayarlar** seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Web uygulamasının IIS ayarlarını denetlemek için

1. **Yönetimsel Araçlar** penceresini açın: **Başlat** menüsünde, **Programlar**' ın üzerine gelin ve **Yönetimsel Araçlar**' a tıklayın. **Yönetimsel Araçlar** **Programlar** menüsünde görünmezse, **Denetim Masası**'nda bu uygulamayı arayın.

   - Windows 2000 ' de **İnternet Hizmetleri Yöneticisi**' i seçin.

   - Windows XP 'de **Internet Information Services**' i seçin.

   - Windows server 2003 ' de **sunucunuzu yönetin**' e çift tıklayın.

        **Sunucunuzu yönetme** penceresi açılır. **Uygulama sunucusu** altında **Bu uygulama sunucusunu yönet**' e tıklayın.

        **Uygulama sunucusu** penceresi açılır. sol bölmedeki **Internet Information Services (ııs) yöneticisi** düğümünü açın.

2. İletişim kutusunda, makineniz için ağaç denetim düğümüne tıklayın. **Web siteleri** düğümüne tıklayın ve Web uygulamasının düğümünü seçin. Bu, bir Web sitesi düğümü ve bu nedenle **varsayılan Web sitesi** düğümünün bir eşdüzey öğesi ya da var olan bir Web sitesi düğümünün altında bir sanal dizin düğümü olacaktır.

3. Web uygulamasına sağ tıklayın ve kısayol menüsünde **Özellikler**' e tıklayın.

4. Web uygulaması için güvenlik ayarlarını doğrulayın:

   1. Web uygulaması **özellikleri** penceresinde, **Dizin Güvenliği** sekmesine tıklayın ve **Düzenle**' ye tıklayın.

   2. **kimlik doğrulama yöntemleri** iletişim kutusunda, henüz seçili değilse **anonim erişimi** ve **tümleşik Windows kimlik doğrulamasını** etkinleştir ' i seçin.

   3. **Kimlik doğrulama yöntemleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. Bir ATL sunucu uygulaması için, hata ayıklama fiilinin ISAPI uzantınızın ilişkili olduğunu doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: uzantı Ile hata ayıklama fiilini ilişkilendirme](/previous-versions/ms165022(v=vs.100)).

6. bir uygulama için, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamanın sanal klasörünün **Internet Information Services (ııs) yöneticisi**, **İnternet Hizmetleri Yöneticisi** veya **Internet Information Services** bir uygulama adı ayarlanmış olduğundan emin olun.

   1. Web uygulaması **Özellikler** penceresinde, uygulama bir sanal dizinde ise veya uygulama bir Web sitesi Ise **giriş dizini** sekmesinde **Dizin** sekmesini seçin.

   2. **Yerel yoldaki** adın, uygulamanın gerçekten dağıtıldığı dizinin adıyla eşleştiğini doğrulayın.

   3. **uygulama Ayarlar** altında, uygulamayı içeren kök dizinin adını yazın.

   4. **Özellikler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

7. bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama için **ASP.NET** sekmesine tıklayın ve doğru sürümünün belirtildiğinden emin olun [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

8. **Özellikler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

9. **Internet Information Services (ııs) yöneticisi**, **İnternet Hizmetleri Yöneticisi** veya **Internet Information Services** iletişim kutusunu kapatmak için **tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorun giderme](../debugger/debugging-web-applications-troubleshooting.md)