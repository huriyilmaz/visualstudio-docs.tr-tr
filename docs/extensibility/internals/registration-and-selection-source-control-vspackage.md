---
title: Kayıt ve Seçim (Kaynak Kontrol VSPackage) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705714"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Kayıt ve Seçim (Kaynak Denetimi VSPackage’ı)
Bir kaynak denetimi VSPackage bunu maruz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bırakmak için kayıtlı olmalıdır. Birden fazla kaynak denetimi VSPackage kayıtlıysa, kullanıcı uygun zamanlarda hangi VSPackage'ı yükleyeceklerini seçebilir. VSPackages hakkında daha fazla bilgi ve bunları nasıl kaydedilene ilişkin daha fazla bilgi için [VSPackages'e](../../extensibility/internals/vspackages.md) bakın.

## <a name="registering-a-source-control-package"></a>Kaynak Kontrol Paketinin Kaydedilmesi
 Kaynak denetim paketi, ortamın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] onu bulabilmesi ve desteklenen özelliklerini sorgulayabilmesi için kaydedilir. Bu, bir paketin bir örneğinin yalnızca özellikleri veya komutları istendiğinde veya açıkça istendiğinde oluşturulduğu bir gecikme yükleme düzenine uygun olarak yapılır.

 VSPackages bilgileri, X'in ana sürüm numarası,\\ *Y'nin* ise küçük sürüm *X* numarası olduğu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*adresindeki bir sürüme özgü kayıt defteri anahtarına yerleştiriyor. Bu uygulama, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]birden çok sürümü yan yana yükleme yi destekleme olanağı sağlar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcı arabirimi (UI), birden çok yüklü kaynak kontrol eklentisi (Kaynak Kontrol Adaptörü Paketi üzerinden) ve kaynak kontrolü VSPackages arasından seçimi destekler. Aynı anda yalnızca bir etkin kaynak kontrol eklentisi veya VSPackage olabilir. Ancak, aşağıda açıklandığı gibi, IDE otomatik çözüm tabanlı paket değiştirme mekanizması ile kaynak kontrol eklentileri ve VSPackages arasında geçiş sağlar. Bu seçim mekanizmasını etkinleştirmek için kaynak denetimi VSPackage'ın bazı gereksinimleri vardır.

### <a name="registry-entries"></a>Kayıt Defteri Girişleri
 Bir kaynak kontrol paketinin üç özel GUID'ye ihtiyacı vardır:

- Paket GUID: Bu, kaynak denetimi uygulamasını içeren paketin ana GUID'idir (bu bölümde ID_Package olarak adlandırılır).

- Kaynak Kontrol GUID: Bu, Visual Studio Kaynak Kontrol Saplaması'na kaydolmak için kullanılan kaynak denetimi VSPackage için bir GUID'dir ve aynı zamanda komut UI bağlamı GUID olarak da kullanılır. Kaynak kontrol hizmeti GUID, kaynak denetimi GUID altında kayıtlıdır. Örnekte, kaynak denetimi GUID ID_SccProvider olarak adlandırılır.

- Kaynak kontrol hizmeti GUID: Bu Visual Studio (bu bölümde SID_SccPkgService denir) tarafından kullanılan özel hizmet GUID olduğunu. Buna ek olarak, kaynak denetim paketinin VSPackages, araç pencereleri ve benzeri diğer GUID'leri tanımlaması gerekir.

  Aşağıdaki kayıt defteri girişleri bir kaynak denetimi VSPackage tarafından yapılmalıdır:

| Anahtar adı | Giriş |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (varsayılan) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (varsayılan) =\<rg_sz: Paket>'nin dostu adı<br /><br /> Hizmet = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (varsayılan) = rg_sz:#\<Yerelleştirilmiş ad> kaynak kimliği<br /><br /> Paket = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Anahtar adı, `SourceCodeControl`, zaten tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanılan ve PackageName> \<için bir seçim olarak kullanılamaz unutmayın.) | (varsayılan) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Kaynak Kontrol Paketi Seçme
 Çeşitli Kaynak Denetimi Eklentisi API tabanlı eklentileri ve kaynak denetimi VSPackages aynı anda kaydedilebilir. Bir kaynak kontrol eklentisi veya VSPackage seçme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] işlemi, eklentiyi veya VSPackage'ı uygun zamanda yükler ve gereksiz bileşenlerin yüklenmeyi gerekli olana kadar erteleyebilir. Ayrıca, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menü öğeleri, iletişim kutuları ve araç çubukları da dahil olmak üzere diğer etkin olmayan VSPackages tüm UI kaldırmak ve etkin VSPackage için UI görüntülemek gerekir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aşağıdaki işlemlerden herhangi biri gerçekleştirildiğinde bir kaynak denetimi VSPackage yükler:

- Çözüm açılır (çözüm kaynak denetimi altındaolduğunda).

   Kaynak denetimi altında bir çözüm veya proje açıldığında, IDE, bu çözüm için belirlenen vspackage kaynak denetiminin yüklenmesine neden olur.

- Kaynak denetimi VSPackage'ın menü komutlarından herhangi biri yürütülür.

  Bir kaynak denetimi VSPackage, yalnızca gerçekten kullanılacağı zaman (aksi takdirde gecikmiş yükleme olarak bilinen) ihtiyacı olan bileşenleri yüklemelidir.

### <a name="automatic-solution-based-vspackage-swapping"></a>Otomatik Çözüm tabanlı VSPackage Takas
 Kaynak Denetimi kategorisi altındaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Seçenekler** iletişim kutusundan kaynak **Source Control** denetimi VSPackages'ı el ile değiştirebilirsiniz. Otomatik çözüm tabanlı paket değiştirme, belirli bir çözüm için belirlenmiş bir kaynak kontrol paketinin, çözüm açıldığında otomatik olarak etkin olarak ayarlandığı anlamına gelir. Her kaynak kontrol <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> paketi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>uygulamalı ve . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hem kaynak denetim eklentileri (Kaynak Denetimi Eklentisi API'sini uygulama) hem de kaynak denetimi VSPackages arasındaki anahtarı işler.

 Kaynak Kontrol Bağdaştırıcı Paketi, herhangi bir Kaynak Kontrol Eklentisi API tabanlı eklentisine geçmek için kullanılır. Ara Kaynak Kontrol Bağdaştırıcı Paketine geçme ve hangi kaynak kontrol eklentisinin etkin veya etkin olmayan olarak ayarlanılması gerektiğini belirleme işlemi kullanıcıya saydamdır. Adaptör Paketi, herhangi bir kaynak kontrol eklentisi etkin olduğunda her zaman etkindir. İki kaynak kontrol eklentisi arasında geçiş yapmak, eklenti DLL'yi yüklemek ve boşaltmak anlamına gelmek anlamına gelmekanlamına gider. Ancak, bir kaynak denetimi VSPackage'a geçmek, uygun VSPackage'ı yüklemek için IDE ile etkileşimi içerir.

 Herhangi bir çözüm açıldığında ve VSPackage'ın kayıt defteri anahtarı çözüm dosyasında olduğunda bir kaynak denetimi VSPackage çağrılır. Çözüm açıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kayıt defteri değerini bulur ve uygun kaynak denetimi VSPackage yükler. Tüm kaynak denetimi VSPackages yukarıda açıklanan kayıt defteri girişleri olmalıdır. Kaynak denetimi altında olan bir çözüm, belirli bir kaynak denetimi VSPackage ile ilişkili olarak işaretlenir. Kaynak kontrolü VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> otomatik çözüm tabanlı VSPackage takas etkinleştirmek için uygulamak gerekir.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Paket Seçimi ve Anahtarlama için Visual Studio UI
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**Kaynak Denetimi** kategorisi altındaki **Seçenekler** iletişim kutusunda kaynak denetimi VSPackage ve eklenti seçimi için bir Kullanıcı Arabirimi sağlar. Kullanıcının etkin kaynak kontrol eklentisini veya VSPackage'ı seçmesini sağlar. Açılan liste şunları içerir:

- Tüm yüklü kaynak kontrol paketleri

- Tüm yüklü kaynak kontrol eklentileri

- Kaynak kodu denetimini devre dışı bırakan "yok" seçeneği

  Etkin kaynak denetimi seçimi için yalnızca UI görünür. VSPackage seçimi önceki VSPackage için UI gizler ve yeni bir ui gösterir. Etkin VSPackage kullanıcı başına olarak seçilir. Bir kullanıcıaynı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] anda açık birden çok kopyası varsa, her biri farklı bir etkin VSPackage kullanabilirsiniz. Aynı bilgisayarda birden çok kullanıcı oturum açmışsa, her [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcının her biri farklı bir etkin VSPackage'a sahip ayrı açık örnekleri olabilir. Birden çok örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir kullanıcı tarafından kapatıldığında, son açık çözüm için etkin olan kaynak denetimi VSPackage, yeniden başlatmada etkin olarak ayarlanacak varsayılan kaynak denetimi VSPackage olur.

  Önceki sürümlerinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]farklı olarak, bir IDE yeniden başlatma artık kaynak denetimi VSPackages geçiş için tek yoldur. VSPackage seçimi otomatiktir. Paketleri değiştirmek için Windows Kullanıcı ayrıcalıkları (Yönetici veya Power User değil) gerekiyor.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
