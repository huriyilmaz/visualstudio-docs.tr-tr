---
title: 'Nasıl yapılır: IIS özellik ayarlarını doğrulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac2ce4f823d82d8a0d8569e15c4ba8920d91d36c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686826"
---
# <a name="how-to-verify-iis-property-settings"></a>Nasıl Yapılır: IIS Özellik Ayarlarını Doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IIS yönetim aracını kullanarak bir Web uygulamasının özelliklerini ayarlayabilirsiniz. Uygulamanın çalışması için bu özelliklerin doğru ayarlanmış olması gerekir, bu nedenle bu ayarların doğrulanması genellikle sorun gidermede gerekli bir adımdır.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Web uygulamasının IIS ayarlarını denetlemek için  
  
1. **Yönetimsel Araçlar** penceresini açın: **Başlat** menüsünde, **Programlar**' ın üzerine gelin ve **Yönetimsel Araçlar**' a tıklayın. **Yönetimsel Araçlar** **Programlar** menüsünde görünmezse, **Denetim Masası**'nda bu uygulamayı arayın.  
  
    - Windows 2000 ' de **İnternet Hizmetleri Yöneticisi**' yi seçin.  
  
    - Windows XP 'de **Internet Information Services**' yi seçin.  
  
    - Windows Server 2003 ' de **Sunucunuzu Yönetin**' e çift tıklayın.  
  
         **Sunucunuzu yönetme** penceresi açılır. **Uygulama sunucusu**altında **Bu uygulama sunucusunu yönet**' e tıklayın.  
  
         **Uygulama sunucusu** penceresi açılır. Sol bölmedeki **Internet Information Services (IIS) Yöneticisi** düğümünü açın.  
  
2. İletişim kutusunda, makineniz için ağaç denetim düğümüne tıklayın. **Web siteleri** düğümüne tıklayın ve Web uygulamasının düğümünü seçin. Bu, bir Web sitesi düğümü ve bu nedenle **varsayılan Web sitesi** düğümünün bir eşdüzey öğesi ya da var olan bir Web sitesi düğümünün altında bir sanal dizin düğümü olacaktır.  
  
3. Web uygulamasına sağ tıklayın ve kısayol menüsünde **Özellikler**' e tıklayın.  
  
4. Web uygulaması için güvenlik ayarlarını doğrulayın:  
  
    1. Web uygulaması **özellikleri** penceresinde, **Dizin Güvenliği** sekmesine tıklayın ve **Düzenle**' ye tıklayın.  
  
    2. **Kimlik doğrulama yöntemleri** iletişim kutusunda, **anonim erişimi etkinleştir** ' i seçin ve henüz seçili değilse **Tümleşik Windows kimlik doğrulamasını** etkinleştirin.  
  
    3. **Kimlik doğrulama yöntemleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
5. Bir ATL sunucu uygulaması için, hata ayıklama fiilinin ISAPI uzantınızın ilişkili olduğunu doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: uzantı Ile hata ayıklama fiilini ilişkilendirme](https://msdn.microsoft.com/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6. Bir uygulama için, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamanın sanal klasörünün **Internet INFORMATION SERVICES (IIS) yöneticisi**, **İnternet Hizmetleri Yöneticisi** veya **Internet Information Services**bir uygulama adı ayarlanmış olduğundan emin olun.  
  
    1. Web uygulaması **Özellikler** penceresinde, uygulama bir sanal dizinde ise veya uygulama bir Web sitesi Ise **giriş dizini** sekmesinde **Dizin** sekmesini seçin.  
  
    2. **Yerel yoldaki** adın, uygulamanın gerçekten dağıtıldığı dizinin adıyla eşleştiğini doğrulayın.  
  
    3. **Uygulama ayarları**' nın altında, uygulamayı içeren kök dizinin adını yazın.  
  
    4. **Özellikler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
7. Bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama için **ASP.net** sekmesine tıklayın ve doğru sürümünün belirtildiğinden emin olun [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
8. **Özellikler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
9. **Internet Information Services (IIS) Yöneticisi**, **İnternet Hizmetleri Yöneticisi**veya **Internet Information Services** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorun giderme](../debugger/debugging-web-applications-troubleshooting.md)
