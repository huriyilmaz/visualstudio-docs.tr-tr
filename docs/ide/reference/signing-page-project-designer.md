---
title: İmzalama Sayfası, Proje Tasarımcısı
description: Uygulama ve dağıtım bildirimlerini imzalamak ve derlemeyi imzalamak için proje Tasarımcısı ' nın Imzalama sayfasını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52d02407316fbc8f9a7b5e3db1c02a3566cda87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957588"
---
# <a name="signing-page-project-designer"></a>İmzalama Sayfası, Proje Tasarımcısı

Uygulama ve dağıtım bildirimlerini imzalamak ve derlemeyi imzalamak (tanımlayıcı ad imzalama) için **Proje Tasarımcısı** ' nın **imzalama** sayfasını kullanın.

Uygulama ve dağıtım bildirimlerinin imzalanmasının, bir derlemenin imzalanmasının dışında bir işlem olduğunu, ancak her iki görevin de **imzalama** sayfasında gerçekleştirildiğinden emin olun.

Ayrıca, anahtar dosya bilgilerinin depolanması, bildirim imzalama ve derleme imzalama için farklılık gösterir. Bildirim imzalama için, anahtar bilgileri bilgisayarınızın şifreleme depolama veritabanında ve geçerli kullanıcının Windows sertifika deposunda depolanır. Derleme imzalama için, anahtar bilgileri yalnızca bilgisayarınızın şifreleme depolama veritabanında depolanır.

**İmzalama** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde **imzalama** sekmesine tıklayın.

## <a name="application-and-deployment-manifest-signing"></a>Uygulama ve dağıtım bildirimi Imzalama

**ClickOnce bildirimlerini imzala** onay kutusu

Uygulama ve dağıtım bildirimlerini bir ortak/özel anahtar çiftiyle imzalamak için bu onay kutusunu işaretleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini imzalama](../../ide/how-to-sign-application-and-deployment-manifests.md).

**Mağaza 'Dan Seç** düğmesi

Geçerli kullanıcının kişisel sertifika deposundan mevcut bir sertifikayı seçmenizi sağlar. Uygulamanızı ve dağıtım bildirimlerinizi imzalamak için bu sertifikalardan birini seçebilirsiniz.

**Mağazadan Seç** ' i tıkladığınızda, kişisel sertifika deponuzda Şu anda geçerli olan ve özel anahtarlara sahip olan sertifikaları listeleyen **bir sertifika seç** iletişim kutusu açılır. Seçtiğiniz sertifikanın amacı kod imzalama içermelidir.

**Sertifika özelliklerini görüntüle**' ye tıklarsanız, **sertifika ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu sertifikayla ilgili ayrıntılı bilgileri içerir ve ek seçenekleri içerir. Ek Yardım bilgilerini görüntülemek için **Sertifikalar hakkında daha fazla bilgi** ' ye tıklayabilirsiniz.

Dosyadan **Seç** düğmesi

Var olan bir anahtar dosyasından bir sertifika seçmenizi sağlar.

Dosyadan **Seç** ' e tıkladığınızda **Dosya Seç** iletişim kutusu açılır. Bu, bir sertifika anahtarı (. pfx) dosyası seçmenizi sağlar. Dosya parola korumalı olmalıdır ve kişisel sertifika deponuzda bulunamaz.

**Dosya açmak için parolayı girin** iletişim kutusunda, sertifika anahtarı (. pfx) dosyasını açmak için bir parola girin. Parola bilgileri kişisel anahtar kapsayıcısı listenizde ve kişisel sertifika deponuzda depolanır.

**Test sertifikası oluştur** düğmesi

Test için bir sertifika oluşturmanıza olanak sağlar. Test sertifikası, ClickOnce uygulamanızı ve dağıtım bildirimlerini imzalamak için kullanılır.

Test **sertifikası oluştur** ' a tıklamak, test sertifikası **Oluştur** iletişim kutusunu açar, burada test sertifikası için tanımlayıcı ad anahtar dosyası için bir parola yazabilirsiniz. Dosya *projectname* _TemporaryKey. pfx olarak adlandırılır. Parola yazmadan **Tamam** ' a tıkladığınızda,. pfx dosyası parola şifrelenmez.

**Zaman damgası sunucusu URL 'si** kutusu

İmzanızın zaman damgasındaki bir sunucunun adresini belirtir. Bir sertifika sağladığınızda, bu dış site uygulamanın imzalandığı saati doğrular.

## <a name="assembly-signing"></a>Bütünleştirilmiş kod Imzalama

**Derlemeyi imzala** onay kutusu

Derlemeyi imzalamak ve kesin adlı bir adlandırılmış anahtar dosyası oluşturmak için bu onay kutusunu seçin. **Proje tasarımcısını** kullanarak derlemeyi imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi Imzalama (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).

Bu seçenek, derlemeyi imzalamak için Windows yazılım geliştirme seti (SDK) tarafından sunulan Al.exe aracını kullanır. Al.exe hakkında daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

**Tanımlayıcı ad anahtar dosyası listesi seçin**

Derlemeyi imzalamak için kullanılan yeni veya var olan bir kesin adlandırılmış anahtar dosyası belirtmenize olanak sağlar. **\<Browse...>** Var olan bir anahtar dosyasını seçmek için seçin.

**\<New...>** Derlemenin imzalanmasını sağlayan yeni bir anahtar dosyası oluşturmayı seçin. Bir anahtar dosya adı belirtmek ve anahtar dosyasını parolayla korumak için kullanabileceğiniz **tanımlayıcı ad anahtarı oluştur** iletişim kutusu görüntülenir. Parola en az 6 karakter uzunluğunda olmalıdır. Bir parola belirtirseniz, kişisel bilgi değişimi (. pfx) dosyası oluşturulur; bir parola belirtmezseniz, kesin adlı bir adlandırılmış anahtar (. snk) dosyası oluşturulur.

**Parola değiştirme** düğmesi

Derlemeyi imzalamak için kullanılan kişisel bilgi değişimi (. pfx) anahtar dosyasının parolasını değiştirir.

**Parolayı Değiştir** ' i tıklatmak, **anahtar parolasını değiştir** iletişim kutusunu açar. Bu iletişim kutusunda **eski parola** , anahtar dosyasının geçerli parolasıdır. **Yeni parola** en az 6 karakter uzunluğunda olmalıdır. Parola bilgileri geçerli kullanıcının Windows sertifika deposunda depolanır.

**Yalnızca gecikmeli imzala** onay kutusu

Gecikmeli imzalamayı etkinleştirmek için bu onay kutusunu işaretleyin.

Bir gecikmeli imzalanmış projenin çalıştırılmadığını ve ayıklanamayacağını unutmayın. Ancak, geliştirme sırasında doğrulamayı atlama seçeneği ile [Sn.exe (tanımlayıcı ad aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool) kullanabilirsiniz `-Vr` .

> [!NOTE]
> Bir derlemeyi imzaladığınızda, her zaman bir özel anahtara erişiminiz olmayabilir. Örneğin, bir kuruluş, geliştiricilerin günlük olarak erişimi olmayan, daha yakından korunan bir anahtar çiftine sahip olabilir. Ortak anahtar kullanılabilir olabilir, ancak özel anahtara erişim birkaç bireyle kısıtlıdır. Böyle bir durumda, ortak anahtar sağlamak için *gecikmeli* veya *kısmi imzalamayı* , derleme kullanıma alınana kadar özel anahtarın eklenmesini ertelemeyi de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Derleme ve Bildirim İmzalamayı Yönetme](../../ide/managing-assembly-and-manifest-signing.md)
- [Nasıl Yapılır: Uygulama ve Dağıtım Bildirimlerini İmzalama](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Nasıl yapılır: derlemeyi Imzalama (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Tanımlayıcı adlı derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
