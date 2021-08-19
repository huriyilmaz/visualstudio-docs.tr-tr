---
title: Kurulum dosyalarını SignTool.exe ile imzalama (ClickOnce)
description: bir kurulum programını ClickOnce uygulamalar için imzalamak üzere SignTool.exe nasıl kullanacağınızı öğrenin. bu, değiştirilen dosyaların yüklü olmamasını sağlamaya yardımcı olur.
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
ms.openlocfilehash: 668c37da5410b0764c9ab84fce44506f8152c68e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160640"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Nasıl yapılır: kurulum dosyalarını SignTool.exe ile Imzalama (ClickOnce)
Bir kurulum programını imzalamak için *SignTool.exe* kullanabilirsiniz (*setup.exe*). Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklü olmamasını sağlamaya yardımcı olur.

 varsayılan olarak, ClickOnce imzalı bildirimler ve imzalı bir kurulum programı vardır. Ancak, Kurulum programının parametrelerini daha sonra değiştirmek istiyorsanız Kurulum programını daha sonra imzalamanız gerekir. Kurulum programı imzalandıktan sonra parametreleri değiştirirseniz, imza bozulur.

 Aşağıdaki yordam imzasız bildirimler ve imzasız bir kurulum programı oluşturur. sonra, imzalı bildirimler oluşturmak için Visual Studio ClickOnce imzalama etkinleştirilir. Müşterinin yürütülebilir dosyayı kendi sertifikasıyla imzalayabilmesi için Kurulum programı imzasız olarak kalır.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>İmzasız bir kurulum programı oluşturmak ve daha sonra imzalamak için

1. Geliştirme bilgisayarında, bildirimleri imzalamak istediğiniz sertifikayı yükleyebilirsiniz.

2. **Çözüm Gezgini** içinde projeyi seçin.

3. **Project** menüsünde, *ProjectName* **özellikler**' e tıklayın.

4. **imzalama** sayfasında **ClickOnce bildirimlerinin** işaretini kaldırın.

5. **Yayımla** sayfasında, **Önkoşullar**' ı tıklatın.

6. Tüm önkoşulların seçili olduğunu doğrulayın ve ardından **Tamam**' a tıklayın.

7. **Yayımla** sayfasında, yayımlama ayarlarını doğrulayın ve **Şimdi Yayımla**' ya tıklayın.

     Çözüm, imzasız uygulama bildirimini, imzasız dağıtım bildirimini, sürüme özgü dosyaları ve imzasız Kurulum programını yayımlama klasörü konumuna yayımlar.

8. **Yayımla** sayfasında, **Önkoşullar**' ı tıklatın.

9. Önkoşul iletişim **kutusunda,** **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** seçimini kaldırın.

10. **Yayımla** sayfasında, yayımlama ayarlarını doğrulayın ve **Şimdi Yayımla**' ya tıklayın.

     Çözüm, imzalı uygulama bildirimini, imzalı dağıtım bildirimini ve sürüme özgü dosyaları yayımlama klasörü konumuna yayımlar. İmzasız Kurulum programı, yayımlama işlemi tarafından üzerine yazılmaz.

11. Müşteri sitesinde bir komut istemi açın.

12. *.exe* dosyasını içeren dizine geçin.

13. *.exe* dosyasını aşağıdaki komutla imzalayın:

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
- [Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
