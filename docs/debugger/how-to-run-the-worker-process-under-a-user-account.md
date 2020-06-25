---
title: Bir kullanıcı hesabı altında bir çalışan işlemi çalıştırın | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac5bee0ffa05aa275782c57fc9b7b1c369bf65d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349412"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Nasıl Yapılır: Çalışan İşlemi Kullanıcı Hesabı Altında Çalıştırma
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Bir kullanıcı hesabı altında çalışan işlemini (aspnet_wp.exe veya w3wp.exe) çalıştırabilmeniz için bilgisayarınızı ayarlamak için aşağıdaki adımları izleyin.

 > [!IMPORTANT]
 > Windows Server 2008 R2 'den başlayarak, her uygulama havuzu için kimlik olarak [Applicationpokaydentity](/iis/manage/configuring-security/application-pool-identities) kullanılması önerilir.

## <a name="procedure"></a>Yordam

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Bir kullanıcı hesabı altında aspnet_wp.exe çalıştırmak için

1. Bilgisayarınızda bulunan machine.config dosyasını, çalışma zamanını yüklediğiniz yolun altındaki yapılandırma klasöründe açın.

2. &lt;ProcessModel bölümünü bulun &gt; ve Kullanıcı ve parola özniteliklerini aspnet_wp.exe altında çalışmasını istediğiniz kullanıcı hesabının adı ve parolasıyla değiştirin.

3. machine.config dosyasını kaydedin.

4. Üzerinde [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] ııs 6,0, varsayılan olarak yüklüdür. Karşılık gelen çalışan işlemi w3wp.exe. Çalışan işlem olarak aspnet_wp.exe IIS 6,0 modunda çalıştırmak için aşağıdaki adımları izlemeniz gerekir:

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

6. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Yapılandırma klasörüyle aynı yolda olması gereken geçici dosyalar klasörünü bulun. Geçici dosyalar klasörüne sağ tıklayın [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve kısayol menüsünde **Özellikler** ' i seçin.

7. **Geçici ASP.NET dosyaları özellikleri** Iletişim kutusunda **güvenlik** sekmesine tıklayın.

8. **Gelişmiş**'e tıklayın.

9. **Geçici ASP.NET dosyaları Için gelişmiş güvenlik ayarları** Iletişim kutusunda **Ekle**' ye tıklayın.

    **Kullanıcı, bilgisayar veya Grup Seç iletişim kutusu** görüntülenir.

10. **Seçilecek nesne adını girin** kutusuna kullanıcı adını yazın ve ardından **Tamam**' a tıklayın. Kullanıcı adının şu biçimde olması gerekir: etkialanı \ KullanıcıAdı

11. **Geçici ASP.NET dosyaları Için Izin girdisi** iletişim kutusunda, kullanıcıya **tam denetim**verin ve ardından **tamam** ' a tıklayarak **Geçici ASP.NET dosyaları için girişi** iletişim kutusunu kapatın.

12. Bir **güvenlik** iletişim kutusu görüntülenir ve bir sistem klasöründeki izinleri gerçekten değiştirmek isteyip istemediğinizi sorar. **Evet**' e tıklayın.

13. **Geçici ASP.NET dosyaları özellikleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [ASP.NET hata ayıklama: sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
