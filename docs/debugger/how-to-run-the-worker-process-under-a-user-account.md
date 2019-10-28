---
title: Bir kullanıcı hesabı altında bir çalışan işlemi çalıştırın | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5905ad87eb534013bdfd786a79e40e46087dff55
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732813"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Nasıl Yapılır: Bir Kullanıcı Hesabı Altında Çalışan İşlemini Çalıştırma
Bilgisayarınızı, bir kullanıcı hesabı altında [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini (Aspnet_wp. exe veya W3wp. exe) çalıştırabilmeniz için ayarlamak üzere aşağıdaki adımları izleyin.

 > [!IMPORTANT]
 > Windows Server 2008 R2 'den başlayarak, her uygulama havuzu için kimlik olarak [Applicationpokaydentity](/iis/manage/configuring-security/application-pool-identities) kullanılması önerilir.

## <a name="procedure"></a>Yordam

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Bir kullanıcı hesabı altında Aspnet_wp.exe çalıştırmak için

1. Çalışma zamanını yüklediğiniz yolun altındaki CONFIG klasöründe bilgisayarınızda bulunan Machine. config dosyasını açın.

2. &lt;processModel&gt; bölümünü bulun ve Kullanıcı ve parola özniteliklerini, Aspnet_wp. exe ' nin altında çalışmasını istediğiniz kullanıcı hesabının adı ve parolasıyla değiştirin.

3. Machine. config dosyasını kaydedin.

4. [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)], IIS 6,0 varsayılan olarak yüklenir. Karşılık gelen çalışan işlem w3wp.exe.To, çalışan işlem olarak Aspnet_wp. exe ile IIS 6,0 modunda çalıştır, aşağıdaki adımları izlemeniz gerekir:

   1. **Başlat**' a, **Yönetimsel Araçlar** ' a ve ardından **Internet Information Services**' yi seçin.

   2. **Internet Information Services** iletişim kutusunda, **Web siteleri** klasörünü sağ tıklatın ve **Özellikler**' i seçin.

   3. **Web siteleri özellikleri** Iletişim kutusunda **hizmet**' i seçin.

   4. **IIS 6.0 yalıtım modunda www hizmetini Çalıştır '** ı seçin.

   5. **Özellikler** iletişim kutusunu kapatın ve **İnternet Hizmetleri Yöneticisi**.

5. Bir Windows komut Istemi açın ve şunu çalıştırarak sunucuyu sıfırlayın:

   ```cmd
   iisreset
   ```

   veya

   ```cmd
   net stop iisadmin /y
   net start w3svc
   ```

6. YAPıLANDıRMA klasörüyle aynı yolda olması gereken geçici [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dosyaları klasörünü bulun. Geçici [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dosyaları klasörüne sağ tıklayın ve kısayol menüsünde **Özellikler** ' i seçin.

7. İçinde **geçici ASP.NET dosyaları özellikleri** iletişim kutusu, tıklayın **güvenlik** sekmesi.

8. **Gelişmiş**'e tıklayın.

9. **Geçici ASP.NET dosyaları Için gelişmiş güvenlik ayarları** Iletişim kutusunda **Ekle**' ye tıklayın.

    **Kullanıcı, bilgisayar veya Grup Seç iletişim kutusu** görüntülenir.

10. **Seçilecek nesne adını girin** kutusuna kullanıcı adını yazın ve ardından **Tamam**' a tıklayın. Kullanıcı adının şu biçimde olması gerekir: EtkiAlanıAdı \ KullanıcıAdı.

11. **Geçici ASP.NET dosyaları Için Izin girdisi** iletişim kutusunda, kullanıcıya **tam denetim**verin ve ardından **tamam** ' a tıklayarak **Geçici ASP.NET dosyaları için girişi** iletişim kutusunu kapatın.

12. Bir **güvenlik** iletişim kutusu görüntülenir ve bir sistem klasöründeki izinleri gerçekten değiştirmek isteyip istemediğinizi sorar. **Evet**'i tıklayın.

13. **Geçici ASP.NET dosyaları özellikleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [ASP.NET hata ayıklaması: Sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
