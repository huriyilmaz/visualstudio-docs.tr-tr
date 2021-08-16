---
title: Kurulum dosyalarını SignTool.exe ile imzalama (ClickOnce)
description: ClickOnce uygulamaları için bir Kurulum programı imzalamak üzere SignTool.exe kullanmayı öğrenin. Bu, üzerinde oynanmış dosyaların yüklenmemelerini sağlamaya yardımcı olur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 7ac7b07a7c01a38221a1420383942b98cd772faac516c3a81cb673075d9cd045
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403867"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Nasıl kullanılır: Kurulum dosyalarını SignTool.exe (ClickOnce)
Bir Kurulum *SignTool.exe* (setup.exe)*imzalamak içinsetup.exe.* Bu işlem, üzerinde oynanmış dosyaların son kullanıcı bilgisayarlarına yüklenmemelerini sağlamaya yardımcı olur.

 Varsayılan olarak, ClickOnce ve imzalı bir Kurulum programı vardır. Ancak, Kurulum programının parametrelerini daha sonra değiştirmek için Kurulum programını daha sonra imzalamanız gerekir. Kurulum programı imzalandıktan sonra parametreleri değiştirirsiniz, imza bozulur.

 Aşağıdaki yordam imzasız bildirimleri ve imzasız bir Kurulum programı üretir. Ardından, ClickOnce bildirimleri oluşturmak için Visual Studio oturum açma özelliği etkindir. Müşterinin yürütülebilir dosyayı kendi sertifikasıyla imzalaması için Kurulum programı imzalanmamış olarak bırakıldı.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>İmzasız kurulum programı oluşturmak ve daha sonra imzalamak için

1. Geliştirme bilgisayarına, bildirimleri imzalamak istediğiniz sertifikayı yükleyin.

2. içinde projeyi **Çözüm Gezgini.**

3. Proje Adı **Project** ProjeAdı *Özellikleri'ne* **tıklayın.**

4. İmzalama **sayfasında,** Oturum **açma bildirimlerinin ClickOnce temizleyebilirsiniz.**

5. Yayımla sayfasında Önkoşullar'a **tıklayın.** 

6. Tüm önkoşulların seçili olduğunu doğrulayın ve ardından Tamam'a **tıklayın.**

7. Yayımla **sayfasında** yayımlama ayarlarını doğrulayın ve Şimdi Yayımla'ya **tıklayın.**

     Çözüm imzasız uygulama bildirimini, imzasız dağıtım bildirimini, sürüme özgü dosyaları ve imzasız Kurulum programını yayımlama klasörü konumunu yayımlar.

8. Yayımla sayfasında Önkoşullar'a **tıklayın.** 

9. **Önkoşullar iletişim** kutusunda Önkoşul bileşenlerini **yüklemek için Kurulum programı oluştur'u temizleyin.**

10. Yayımla **sayfasında** yayımlama ayarlarını doğrulayın ve Şimdi Yayımla'ya **tıklayın.**

     Çözüm, imzalı uygulama bildirimini, imzalı dağıtım bildirimini ve sürüme özgü dosyaları yayımlama klasörü konumunu yayımlar. Yayımlama işlemi imzasız Kurulum programının üzerine yazılmaz.

11. Müşteri sitesinde bir komut istemi açın.

12. .exedosyasını *içeren.exe.*

13. .exe *dosyasını* aşağıdaki komutla imzalar:

    ```cmd
    signtool sign /sha1 CertificateHash Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

     Örneğin, Kurulum programını imzalamak için aşağıdaki komutlardan birini kullanın:

    ```cmd
    signtool sign /sha1 CCB... Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılanlar: Uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
