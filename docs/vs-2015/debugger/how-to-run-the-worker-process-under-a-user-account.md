---
title: 'Nasıl yapılır: bir kullanıcı hesabı altında çalışan Işlemini çalıştırma | Microsoft Docs'
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
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157864"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Nasıl Yapılır: Çalışan İşlemi Kullanıcı Hesabı Altında Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Bir kullanıcı hesabı altında çalışan işlemini (aspnet_wp.exe veya w3wp.exe) çalıştırabilmeniz için bilgisayarınızı ayarlamak için aşağıdaki adımları izleyin.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Bir kullanıcı hesabı altında aspnet_wp.exe çalıştırmak için  
  
1. Bilgisayarınızda bulunan machine.config dosyasını, çalışma zamanını yüklediğiniz yolun altındaki yapılandırma klasöründe açın.  
  
2. &lt;ProcessModel bölümünü bulun &gt; ve Kullanıcı ve parola özniteliklerini aspnet_wp.exe altında çalışmasını istediğiniz kullanıcı hesabının adı ve parolasıyla değiştirin.  
  
3. machine.config dosyasını kaydedin.  
  
4. Üzerinde [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)] ııs 6,0, varsayılan olarak yüklüdür. Karşılık gelen çalışan işlemi w3wp.exe. Çalışan işlem olarak aspnet_wp.exe IIS 6,0 modunda çalıştırmak için aşağıdaki adımları izlemeniz gerekir:  
  
    1. **Başlat**' a, **Yönetimsel Araçlar** ' a ve ardından **Internet Information Services**' yi seçin.  
  
    2. **Internet Information Services** iletişim kutusunda, **Web siteleri** klasörünü sağ tıklatın ve **Özellikler**' i seçin.  
  
    3. **Web siteleri özellikleri** Iletişim kutusunda **hizmet**' i seçin.  
  
    4. **IIS 6.0 yalıtım modunda www hizmetini Çalıştır '** ı seçin.  
  
    5. **Özellikler** iletişim kutusunu kapatın ve **İnternet Hizmetleri Yöneticisi**.  
  
5. Bir Windows komut Istemi açın ve şunu çalıştırarak sunucuyu sıfırlayın:  
  
    ```  
    iisreset  
    ```  

    veya  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Yapılandırma klasörüyle aynı yolda olması gereken geçici dosyalar klasörünü bulun. Geçici dosyalar klasörüne sağ tıklayın [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ve kısayol menüsünde **Özellikler** ' i seçin.  
  
7. **Geçici ASP.NET dosyaları özellikleri** Iletişim kutusunda **güvenlik** sekmesine tıklayın.  
  
8. **Gelişmiş**'e tıklayın.  
  
9. **Geçici ASP.NET dosyaları Için gelişmiş güvenlik ayarları** Iletişim kutusunda **Ekle**' ye tıklayın.  
  
    **Kullanıcı, bilgisayar veya Grup Seç iletişim kutusu** görüntülenir.  
  
10. **Seçilecek nesne adını girin** kutusuna kullanıcı adını yazın ve ardından **Tamam**' a tıklayın. Kullanıcı adının şu biçimde olması gerekir: etkialanı \ KullanıcıAdı  
  
11. **Geçici ASP.NET dosyaları Için Izin girdisi** iletişim kutusunda, kullanıcıya **tam denetim**verin ve ardından **tamam** ' a tıklayarak **Geçici ASP.NET dosyaları için girişi** iletişim kutusunu kapatın.  
  
12. Bir **güvenlik** iletişim kutusu görüntülenir ve bir sistem klasöründeki izinleri gerçekten değiştirmek isteyip istemediğinizi sorar. **Evet**'e tıklayın.  
  
13. **Geçici ASP.NET dosyaları özellikleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[ASP.NET hata ayıklama: sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)  
