---
title: İmzalama sayfası, proje Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5707ef277892c37cab16f78ac11113194a95e190
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663511"
---
# <a name="signing-page-project-designer"></a>İmzalama Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uygulama ve dağıtım bildirimlerini imzalamak ve derlemeyi imzalamak (tanımlayıcı ad imzalama) için **Proje Tasarımcısı** ' nın **imzalama** sayfasını kullanın.

 Uygulama ve dağıtım bildirimlerinin imzalanmasının, bir derlemenin imzalanmasının dışında bir işlem olduğunu, ancak her iki görevin de **imzalama** sayfasında gerçekleştirildiğinden emin olun.

 Ayrıca, anahtar dosya bilgilerinin depolanması, bildirim imzalama ve derleme imzalama için farklılık gösterir. Bildirim imzalama için, anahtar bilgileri bilgisayarınızın şifreleme depolama veritabanında ve geçerli kullanıcının Windows sertifika deposunda depolanır. Derleme imzalama için, anahtar bilgileri yalnızca bilgisayarınızın şifreleme depolama veritabanında depolanır.

 **İmzalama** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde **imzalama** sekmesine tıklayın.

## <a name="application-and-deployment-manifest-signing"></a>Uygulama ve dağıtım bildirimi Imzalama
 **ClickOnce bildirimlerini imzala** onay kutusu, uygulama ve dağıtım bildirimlerini bir ortak/özel anahtar çiftiyle imzalamak için bu onay kutusunu işaretleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini imzalama](../../ide/how-to-sign-application-and-deployment-manifests.md).

 **Mağaza 'Dan Seç** düğmesi geçerli kullanıcının kişisel sertifika deposundan var olan bir sertifikayı seçmenizi sağlar. Uygulamanızı ve dağıtım bildirimlerinizi imzalamak için bu sertifikalardan birini seçebilirsiniz.

 **Mağazadan Seç** ' i tıkladığınızda, kişisel sertifika deponuzda Şu anda geçerli olan ve özel anahtarlara sahip olan sertifikaları listeleyen **bir sertifika seç** iletişim kutusu açılır. Seçtiğiniz sertifikanın amacı kod imzalama içermelidir.

 **Sertifika özelliklerini görüntüle**' ye tıklarsanız, **sertifika ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu sertifikayla ilgili ayrıntılı bilgileri içerir ve ek seçenekleri içerir. Ek Yardım bilgilerini görüntülemek için **Sertifikalar hakkında daha fazla bilgi** ' ye tıklayabilirsiniz.

 Dosyadan **Seç** düğmesi var olan bir anahtar dosyasından bir sertifika seçmenizi sağlar.

 Dosyadan **Seç** ' e tıkladığınızda **Dosya Seç** iletişim kutusu açılır. Bu, bir sertifika anahtarı (. pfx) dosyası seçmenizi sağlar. Dosya parola korumalı olmalıdır ve kişisel sertifika deponuzda bulunamaz.

 **Dosya açmak için parolayı girin** iletişim kutusunda, sertifika anahtarı (. pfx) dosyasını açmak için bir parola girin. Parola bilgileri kişisel anahtar kapsayıcısı listenizde ve kişisel sertifika deponuzda depolanır.

 **Test sertifikası oluştur** düğmesi test için bir sertifika oluşturmanıza olanak sağlar. Test sertifikası, ClickOnce uygulamanızı ve dağıtım bildirimlerini imzalamak için kullanılır.

 Test **sertifikası oluştur** ' a tıklamak, test sertifikası **Oluştur** iletişim kutusunu açar, burada test sertifikası için tanımlayıcı ad anahtar dosyası için bir parola yazabilirsiniz. Dosya *ProjectName*_TemporaryKey. pfx olarak adlandırılır. Parola yazmadan **Tamam** ' a tıkladığınızda,. pfx dosyası parola şifrelenmez.

 **Zaman damgası sunucusu URL 'si** kutusu, imzanızın zaman damgasında bir sunucunun adresini belirtir. Bir sertifika sağladığınızda, bu dış site uygulamanın imzalandığı saati doğrular.

## <a name="assembly-signing"></a>Bütünleştirilmiş kod Imzalama
 **Derlemeyi imzala** onay kutusu, derlemeyi imzalamak ve kesin adlandırılmış anahtar dosyası oluşturmak için bu onay kutusunu işaretleyin. **Proje tasarımcısını**kullanarak derlemeyi imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi Imzalama (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).

 Bu seçenek, derlemeyi imzalamak için [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] tarafından sunulan al. exe aracını kullanır. Al. exe hakkında daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 **Tanımlayıcı ad anahtar dosyası** listesi, derlemeyi imzalamak için kullanılan yeni veya var olan bir kesin adlandırılmış anahtar dosyası belirtmenize olanak sağlar. **@No__t_1Browse seçin...** mevcut bir anahtar dosyasını seçmek için >.

 **@No__t_1New seçin...** derlemenin imzalanmasını sağlayan yeni bir anahtar dosyası oluşturmak için >. Bir anahtar dosya adı belirtmek ve anahtar dosyasını parolayla korumak için kullanabileceğiniz **tanımlayıcı ad anahtarı oluştur** iletişim kutusu görüntülenir. Parola en az 6 karakter uzunluğunda olmalıdır. Bir parola belirtirseniz, kişisel bilgi değişimi (. pfx) dosyası oluşturulur; bir parola belirtmezseniz, kesin adlı bir adlandırılmış anahtar (. snk) dosyası oluşturulur.

 **Parola Değiştir** düğmesi, derlemeyi imzalamak Için kullanılan kişisel bilgi değişimi (. pfx) anahtar dosyasının parolasını değiştirir.

 **Parolayı Değiştir** ' i tıklatmak, **anahtar parolasını değiştir** iletişim kutusunu açar. Bu iletişim kutusunda **eski parola** , anahtar dosyasının geçerli parolasıdır. **Yeni parola** en az 6 karakter uzunluğunda olmalıdır. Parola bilgileri geçerli kullanıcının Windows sertifika deposunda depolanır.

 **Yalnızca IMZALAMAYı geciktir** onay kutusu, Gecikmeli imzalamayı etkinleştirmek için bu onay kutusunu işaretleyin.

 Bir gecikmeli imzalanmış projenin çalıştırılmadığını ve ayıklanamayacağını unutmayın. Ancak, geliştirme sırasında doğrulamayı atlamak için `-Vr` seçeneğiyle [sn. exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) kullanabilirsiniz.

> [!NOTE]
> Bir derlemeyi imzaladığınızda, her zaman bir özel anahtara erişiminiz olmayabilir. Örneğin, bir kuruluş, geliştiricilerin günlük olarak erişimi olmayan, daha yakından korunan bir anahtar çiftine sahip olabilir. Ortak anahtar kullanılabilir olabilir, ancak özel anahtara erişim birkaç bireyle kısıtlıdır. Böyle bir durumda, ortak anahtar sağlamak için *gecikmeli* veya *kısmi imzalamayı* , derleme kullanıma alınana kadar özel anahtarın eklenmesini ertelemeyi de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje Özellikleri başvurusu](../../ide/reference/project-properties-reference.md) [derleme ve bildirim IMZALAMAYı yönetme](../../ide/managing-assembly-and-manifest-signing.md) [yönetilen uygulamalar için tanımlayıcı ad IMZALAMAYı](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5) Imzalama [nasıl yapılır: uygulama ve dağıtım bildirimlerini](../../ide/how-to-sign-application-and-deployment-manifests.md) Imzalama [nasıl yapılır: bir derlemeyi imzalama (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564) [Nasıl yapılır: tanımlayıcı adı kesin adlandırılmış Derlemelerle bir derlemeyi imzalama](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
