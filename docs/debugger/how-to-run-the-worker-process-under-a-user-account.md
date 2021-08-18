---
title: Bir kullanıcı hesabı altında bir çalışan işlemi çalıştırın | Microsoft Docs
description: bilgisayarınızı, Visual Studio içindeki bir kullanıcı hesabı altında ASP.NET çalışan işlemini (aspnet_wp.exe veya w3wp.exe) çalıştırabilmeniz için ayarlayın.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e9bf2b73d83f2a55bc9b8c370eff6036265dcea6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097213"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Nasıl Yapılır: Çalışan İşlemi Kullanıcı Hesabı Altında Çalıştırma
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Bir kullanıcı hesabı altında çalışan işlemini (aspnet_wp.exe veya w3wp.exe) çalıştırabilmeniz için bilgisayarınızı ayarlamak için aşağıdaki adımları izleyin.

 > [!IMPORTANT]
 > Windows Server 2008 R2 'den başlayarak, her uygulama havuzu için kimlik olarak [applicationpokaydentity](/iis/manage/configuring-security/application-pool-identities) kullanılması önerilir.

## <a name="procedure"></a>Yordam

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Bir kullanıcı hesabı altında aspnet_wp.exe çalıştırmak için

1. Bilgisayarınızda bulunan machine.config dosyasını, çalışma zamanını yüklediğiniz yolun altındaki yapılandırma klasöründe açın.

2. &lt;ProcessModel bölümünü bulun &gt; ve Kullanıcı ve parola özniteliklerini aspnet_wp.exe altında çalışmasını istediğiniz kullanıcı hesabının adı ve parolasıyla değiştirin.

3. machine.config dosyasını kaydedin.

4. Üzerinde [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] ııs 6,0, varsayılan olarak yüklüdür. Karşılık gelen çalışan işlemi w3wp.exe. Çalışan işlem olarak aspnet_wp.exe IIS 6,0 modunda çalıştırmak için aşağıdaki adımları izlemeniz gerekir:

   1. **başlat**' a, **yönetimsel araçlar** ' a ve ardından **Internet Information Services**' yi seçin.

   2. **Internet Information Services** iletişim kutusunda, **Web siteleri** klasörünü sağ tıklatın ve **özellikler**' i seçin.

   3. **Web siteleri özellikleri** Iletişim kutusunda **hizmet**' i seçin.

   4. **IIS 6.0 yalıtım modunda www hizmetini Çalıştır '** ı seçin.

   5. **Özellikler** iletişim kutusunu kapatın ve **İnternet Hizmetleri Yöneticisi**.

5. Windows bir komut istemi açın ve şunu çalıştırarak sunucuyu sıfırlayın:

   ```cmd
   iisreset
   ```

   veya

   ```cmd
   net stop iisadmin /y
   net start w3svc
   ```

6. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Yapılandırma klasörüyle aynı yolda olması gereken geçici dosyalar klasörünü bulun. Geçici dosyalar klasörüne sağ tıklayın [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve kısayol menüsünde **Özellikler** ' i seçin.

7. **geçici ASP.NET dosyaları özellikleri** iletişim kutusunda **güvenlik** sekmesine tıklayın.

8. **Gelişmiş**'e tıklayın.

9. **geçici ASP.Net dosyaları için gelişmiş güvenlik Ayarlar** iletişim kutusunda **ekle**' ye tıklayın.

    **Kullanıcı, bilgisayar veya Grup Seç iletişim kutusu** görüntülenir.

10. **Seçilecek nesne adını girin** kutusuna kullanıcı adını yazın ve ardından **Tamam**' a tıklayın. Kullanıcı adının şu biçimde olması gerekir: etkialanı \ KullanıcıAdı

11. **geçici ASP.NET dosyaları için izin girişi** iletişim kutusunda kullanıcıya **tam denetim** verin ve ardından **geçici ASP.NET dosyalar** iletişim kutusunu kapatmak için **tamam** ' a tıklayın.

12. Bir **güvenlik** iletişim kutusu görüntülenir ve bir sistem klasöründeki izinleri gerçekten değiştirmek isteyip istemediğinizi sorar. **Evet**'e tıklayın.

13. **geçici ASP.NET dosyaları özellikleri** iletişim kutusunu kapatmak için **tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET uygulamalarda hata ayıkla](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [ASP.NET Hata ayıklama: sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
