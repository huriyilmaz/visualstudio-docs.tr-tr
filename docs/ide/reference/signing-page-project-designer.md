---
title: İmzalama Sayfası, Proje Tasarımcısı
description: Uygulama ve dağıtım bildirimlerini imzalamak için Project Tasarımcısı'nın İmzalama sayfasını ve ayrıca derlemeyi imzalamak için kullanın.
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
ms.openlocfilehash: e287821ad2419d8c8e5f3e33567e874a995fed999867800998e5cb358166a75b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271736"
---
# <a name="signing-page-project-designer"></a>İmzalama Sayfası, Proje Tasarımcısı

Uygulama **ve dağıtım** **bildirimlerini imzalamak ve derlemeyi** (güçlü ad imzalama) imzalamak için Project Tasarımcısı'nın İmzalama sayfasını kullanın.

Her iki görev de İmzalama sayfasında gerçekleştirilse de, uygulama ve dağıtım bildirimlerinin imzalanması, derlemenin imzalanmasından ayrı bir **işlemdir.**

Ayrıca, anahtar dosyası bilgilerini depolama, bildirim imzalama ve derleme imzalama için farklılık gösterir. Bildirim imzalama için, anahtar bilgileri bilgisayarınızın şifreleme depolama veritabanında ve geçerli kullanıcının sertifika Windows depolanır. Derleme imzalama için anahtar bilgileri yalnızca bilgisayarınızın şifreleme depolama veritabanında depolanır.

İmzalama sayfasına **erişmek** için, Çözüm Gezgini'de bir proje düğümü seçin ve  **Project'a** **tıklayın.** Project **Tasarımcısı** göründüğünde İmzalama **sekmesine** tıklayın.

## <a name="application-and-deployment-manifest-signing"></a>Uygulama ve Dağıtım Bildirimi İmzalama

**Bildirim ClickOnce kutusunu** imzalama

Uygulamayı ve dağıtım bildirimlerini ortak/özel anahtar çifti ile imzalamak için bu onay kutusunu seçin. Bunun nasıl olduğu hakkında daha fazla bilgi için, [bkz. How to: Sign Application and Deployment Manifests](../../ide/how-to-sign-application-and-deployment-manifests.md).

**Mağaza düğmesinden** seçin

Geçerli kullanıcının kişisel sertifika depolamadan mevcut bir sertifikayı seçmenize olanak sağlar. Uygulama ve dağıtım bildirimlerinizi imzalamak için bu sertifikalardan birini kullanabilirsiniz.

Depodan **Seç'e** tıklarsa, kişisel sertifika deponda geçerli (süresi dolmadı) ve özel anahtarlara sahip sertifikaları listelenin Bir Sertifika Seç iletişim kutusu açılır.  Seçerek sertifikanın amacı kod imzalamayı içermesi gerekir.

Sertifika özelliklerini **görüntüle'ye tıklarsanız** **Sertifika Ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu sertifika hakkında ayrıntılı bilgiler ve ek seçenekler içerir. Ek Yardım bilgilerini **görüntülemek için Sertifikalar hakkında daha fazla bilgi** edin'e tıkabilirsiniz.

**Dosya düğmesinden** seçin

Var olan bir anahtar dosyasından sertifika seçmenize olanak sağlar.

Dosyadan **Seç'e** **tıklarsanız,** bir sertifika anahtarı (.pfx) dosyası seçmenize olanak sağlayan Dosya Seç iletişim kutusu açılır. Dosyanın parola korumalı olması gerekir ve kişisel sertifika deponda zaten bulunamaz.

Dosya **açmak için parola girin iletişim** kutusunda, sertifika anahtarı (.pfx) dosyasını açmak için bir parola girin. Parola bilgileri kişisel anahtar kapsayıcısı listeniz ve kişisel sertifika deponda depolanır.

**Test Sertifikası Oluştur** düğmesi

Test etmek için bir sertifika oluşturmanıza olanak sağlar. Test sertifikası, uygulama ve dağıtım ClickOnce imzalamak için kullanılır.

Test **Sertifikası Oluştur'a** tıklarsanız, **test** sertifikası için güçlü ad anahtar dosyası için bir parola yazarak Test Sertifikası Oluştur iletişim kutusu açılır. Dosya, *projectname* _TemporaryKey.pfx olarak adlandırılmıştır. Parola **yazmadan** Tamam'a tıklarsanız.pfx dosyası parolayla şifrelenmez.

**Zaman damgası sunucusu URL'si** kutusu

İmzanızı zaman damgasına alan sunucunun adresini belirtir. Bir sertifika sağlarken, bu dış site uygulamanın imza olduğu zamanı doğrular.

## <a name="assembly-signing"></a>Derleme İmzalama

**Derleme onay** kutusunu imzalama

Derlemeyi imzalamak ve kesin adlandırılmış bir anahtar dosyası oluşturmak için bu onay kutusunu seçin. Project Designer'ı kullanarak derlemeyi imzalama hakkında daha fazla **bilgi için,** [bkz. Nasıl kullanılır: Derlemeyi İmzalama (Visual Studio).](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)

Bu seçenek, derlemeyi Al.exe için Windows Yazılım Geliştirme Seti (SDK) tarafından sağlanan Al.exe aracını kullanır. Derleme hakkında daha fazla Al.exe için, [bkz. How to: Sign an Assembly with a Strong Name](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

**Bir güçlü ad anahtar dosyası listesi** seçin

Derlemeyi imzalamak için kullanılan yeni veya kesin adlandırılmış bir anahtar dosyası belirtmenizi sağlar. Var **\<Browse...>** olan bir anahtar dosyasını seçmek için öğesini seçin.

Derlemeyi **\<New...>** imzalamak için yeni bir anahtar dosyası oluşturmak için öğesini seçin. Anahtar **dosyası adı belirtmek** ve anahtar dosyasını parolayla korumak için kullanabileceğiniz Güçlü Ad Anahtarı Oluştur iletişim kutusu görüntülenir. Parola en az 6 karakter uzunluğunda olmalıdır. Bir parola belirtirseniz, Kişisel Bilgiler Exchange (.pfx) dosyası oluşturulur; Parola belirtmezseniz, kesin olarak adlandırılmış bir anahtar (.snk) dosyası oluşturulur.

**Parolayı Değiştir** düğmesi

Derlemeyi imzalamak için kullanılan Exchange (.pfx) anahtar dosyasının parolasını değiştirir.

Parolayı **Değiştir'e** **tıklarsanız Anahtar Parolasını Değiştir iletişim** kutusu açılır. Bu iletişim kutusunda Eski **parola,** anahtar dosyasının geçerli parolasıdır. **Yeni parola** en az 6 karakter uzunluğunda olmalıdır. Parola bilgileri, geçerli kullanıcının sertifika depolama Windows depolanır.

**Yalnızca imzalamayı geciktir** onay kutusu

Gecikmeli imzalamayı etkinleştirmek için bu onay kutusunu seçin.

Gecikmeli imzalı bir projenin çalışmay olacağını ve hata ayıklanamayacaklarını unutmayın. Ancak geliştirme sırasında doğrulamayı atlamaSn.exe aracı [ (Güçlü](/dotnet/framework/tools/sn-exe-strong-name-tool) Ad Aracı) `-Vr` seçeneğini kullanabilirsiniz.

> [!NOTE]
> Bir derlemeyi imzalarken her zaman özel anahtara erişiminizin olmaz. Örneğin, bir kuruluş, geliştiricilerin günlük erişime sahip olmadığını yakından korumalı bir anahtar çifti olabilir. Ortak anahtar kullanılabilir, ancak özel anahtara erişim birkaç birey ile sınırlıdır. Böyle bir durumda, ortak  anahtarı  sağlamak için gecikmeli veya kısmi imzalama kullanabilir, derleme devredilene kadar özel anahtarın eksini erteleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Derleme ve Bildirim İmzalamayı Yönetme](../../ide/managing-assembly-and-manifest-signing.md)
- [Nasıl Yapılır: Uygulama ve Dağıtım Bildirimlerini İmzalama](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Nasıl: Derlemeyi İmzala (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Güçlü Adlandırılmış Derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
