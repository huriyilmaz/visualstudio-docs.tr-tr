---
title: Bir kullanıcı hesabı hesabı altında çalışan işlemi | Microsoft Docs
description: ASP.NET çalışan işlemini (aspnet_wp.exe veya w3wp.exe) bir kullanıcı hesabı altında çalıştıracak şekilde bilgisayarınızı Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0c9e9812bb2a657d95f0a5a2d477d49995f79bb3
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971666"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Nasıl Yapılır: Çalışan İşlemi Kullanıcı Hesabı Altında Çalıştırma
Bir kullanıcı hesabı altında çalışan işlemini (aspnet_wp.exe veya w3wp.exe) çalıştıracak şekilde bilgisayarınızı ayarlamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aşağıdaki adımları izleyin.

 > [!IMPORTANT]
 > Windows Server 2008 R2'den başlayarak, her uygulama havuzu için kimlik olarak [ApplicationPoolIdentity'nin](/iis/manage/configuring-security/application-pool-identities) kullanılması önerilir.

## <a name="procedure"></a>Yordam

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Bir kullanıcı aspnet_wp.exe altında bir hesabı çalıştırmak için

1. Çalışma machine.config yolunun altındaki CONFIG klasöründe bulunan bir dosya açın.

2. processModel bölümünü bulun ve kullanıcı ve parola özniteliklerini, altında çalıştırmak istediğiniz kullanıcı &lt; &gt; hesabının adı aspnet_wp.exe değiştirebilirsiniz.

3. machine.config kaydedin.

4. üzerinde [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] IIS 6.0 varsayılan olarak yüklenir. Karşılık gelen çalışan işlemi w3wp.exe. Çalışan işlemi olarak aspnet_wp.exe IIS 6.0 modunda çalıştırmak için şu adımları izlemelisiniz:

   1. **Başlat'a** tıklayın, **Yönetimsel Araçlar'a** tıklayın ve ardından **Internet Information Services.**

   2. Internet Information Services **iletişim** kutusunda Web Siteleri klasörüne sağ **tıklayın** ve Özellikler'i **seçin.**

   3. Web Siteleri **Özellikleri iletişim kutusunda** Hizmet'i **seçin.**

   4. **IIS6.0 yalıtım modunda WWW hizmetini çalıştır'ı seçin.**

   5. Özellikler iletişim **kutusunu** kapatın ve **İnternet Hizmetleri Yöneticisi.**

5. Aşağıdaki komutu Windows komut istemini açın ve sunucuyu sıfırlayın:

   ```cmd
   iisreset
   ```

   — veya —

   ```cmd
   net stop iisadmin /y
   net start w3svc
   ```

6. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]CONFIG klasörüyle aynı yolda olması gereken Geçici Dosyalar klasörünü bulun. Geçici Dosyalar klasörüne sağ [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tıklayın ve kısayol menüsünde **Özellikler'i** seçin.

7. Geçici **ASP.NET Dosyaları Özellikleri** iletişim kutusunda Güvenlik **sekmesine** tıklayın.

8. **Gelişmiş**'e tıklayın.

9. Geçici Dosyalar **için Ayarlar Gelişmiş Güvenlik ASP.Net iletişim kutusunda** Ekle'ye **tıklayın.**

    Kullanıcı, **Bilgisayar veya Grup Seç iletişim kutusu** görüntülenir.

10. Seçki olarak nesne adını **girin kutusuna kullanıcı adını yazın** ve ardından Tamam'a **tıklayın.** Kullanıcı adı şu biçimde olmalıdır: DomainName\UserName.

11. Geçici **ASP.NET** Dosyaları için İzin Girdisi iletişim kutusunda, kullanıcıya Tam Denetim'i girin ve ardından Tamam'a tıklar ve Geçici ASP.NET Için Girdi **iletişim** kutusunu kapatın. 

12. Bir **Güvenlik** iletişim kutusu görüntülenir ve sistem klasöründeki izinleri gerçekten değiştirmek istiyor sanız sorar. **Evet**'e tıklayın.

13. Geçici **Dosya** Özellikleri iletişim kutusunu **kapatmak ASP.NET Tamam'a** tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET Uygulamalarında Hata Ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [ASP.NET Hata Ayıklama: Sistem Gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
