---
title: Kayıt ve seçim (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d6ca60c74ae9956f38418ea6048bb0c8050be2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724513"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Kayıt ve Seçim (Kaynak Denetimi VSPackage’ı)
Kaynak denetimi VSPackage 'ın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] göstermek için kayıtlı olması gerekir. Birden fazla kaynak denetimi VSPackage kayıtlıysa, Kullanıcı hangi VSPackage 'ın uygun zamanlarda yükleneceğini seçebilir. VSPackages hakkında daha fazla ayrıntı ve bunların nasıl kaydedileceği hakkında bilgi için bkz. [VSPackages](../../extensibility/internals/vspackages.md) .

## <a name="registering-a-source-control-package"></a>Kaynak denetim paketini kaydetme
 Kaynak denetim paketi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortamının onu bulabileceği ve desteklenen özellikleri için Sorgulayabileceğiniz şekilde kaydedilir. Bu, bir paket örneğinin yalnızca özellikleri veya komutları gerekli olduğunda ya da açıkça istendiği zaman oluşturulduğu bir gecikme yükleme şemasına göre yapılır.

 VSPackages, bilgileri sürüme özgü bir kayıt defteri anahtarına HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*x. Y*, burada *x* büyük sürüm numarası ve *Y* ise ikincil sürüm numarasıdır. Bu uygulama, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birden çok sürümünün yan yana yüklenmesini destekleme yeteneği sağlar.

 @No__t_0 Kullanıcı arabirimi (UI), birden fazla yüklü kaynak denetimi eklentisi arasından (kaynak denetim bağdaştırıcısı paketi aracılığıyla) seçim ve kaynak denetimi VSPackages 'yi destekler. Tek seferde yalnızca bir etkin kaynak denetimi eklentisi veya VSPackage olabilir. Bununla birlikte, aşağıda açıklandığı gibi IDE, otomatik çözüm tabanlı bir paket değiştirme mekanizması aracılığıyla kaynak denetimi eklentileri ve VSPackages arasında geçiş yapılmasına izin verir. Bu seçim mekanizmasını etkinleştirmek için VSPackage kaynak denetiminin bölümünde bazı gereksinimler vardır.

### <a name="registry-entries"></a>Kayıt defteri girdileri
 Kaynak denetim paketinde üç özel GUID gerekir:

- Paket GUID 'SI: Bu, kaynak denetim uygulamasını içeren paketin ana GUID 'sidir (Bu bölümde ID_Package olarak adlandırılır).

- Kaynak denetimi GUID 'SI: Bu, Visual Studio kaynak denetimi saplamaya kaydolmak için kullanılan VSPackage için bir GUID 'dir ve ayrıca bir komut UI bağlamı GUID 'SI olarak da kullanılır. Kaynak denetimi hizmeti GUID 'SI, kaynak denetimi GUID 'sinin altına kaydedilir. Örnekte, kaynak denetimi GUID 'SI ID_SccProvider olarak adlandırılır.

- Kaynak denetimi hizmeti GUID 'SI: Bu, Visual Studio tarafından kullanılan özel hizmet GUID 'sidir (Bu bölümde SID_SccPkgService olarak adlandırılır). Buna ek olarak, kaynak denetimi paketinin VSPackages, araç pencereleri vb. için diğer GUID 'Leri tanımlanması gerekir.

  Aşağıdaki kayıt defteri girdilerinin bir kaynak denetimi VSPackage tarafından yapılması gerekir:

| Anahtar adı | Girişleriyle |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (varsayılan) = RG_SZ: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (varsayılan) = RG_SZ: \<Friendly paketin adı ><br /><br /> Hizmet = RG_SZ: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (varsayılan) = RG_SZ: yerelleştirilmiş ad için # \<Resource KIMLIĞI ><br /><br /> Paket = RG_SZ: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (@No__t_0 anahtar adının [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tarafından zaten kullanıldığını ve \<PackageName > için seçim olarak kullanılamayacağını unutmayın.) | (varsayılan) = RG_SZ: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Kaynak denetim paketi seçme
 Çeşitli kaynak denetimi eklentisi API tabanlı eklentiler ve kaynak denetimi VSPackages, eşzamanlı olarak kaydedilmiş olabilir. Kaynak denetimi eklentisi veya VSPackage seçme işlemi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentinin veya VSPackage 'ın uygun zamanda yüklenmesini sağlamalıdır ve gerekli olana kadar gereksiz bileşenleri yüklemeyi erteleyebilirsiniz. Ayrıca, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menü öğeleri, iletişim kutuları ve araç çubukları da dahil olmak üzere diğer etkin olmayan VSPackages öğelerinden tüm Kullanıcı arabirimini kaldırması ve etkin VSPackage için Kullanıcı arabirimini görüntülemesi gerekir.

 Aşağıdaki işlemlerden herhangi biri gerçekleştirildiğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir kaynak denetimi VSPackage yükler:

- Çözüm açıldı (çözüm kaynak denetimi altında olduğunda).

   Kaynak denetimi altındaki bir çözüm veya proje açıldığında, IDE, bu çözüm için ayrılmış kaynak denetimi VSPackage 'ın yüklenmesine neden olur.

- VSPackage kaynak denetiminin herhangi bir menü komutu yürütülür.

  Kaynak denetimi VSPackage, ihtiyaç duydukları tüm bileşenleri yalnızca gerçekten kullanılacaksa (yani Gecikmeli yükleme olarak bilinir) yüklemesi gerekir.

### <a name="automatic-solution-based-vspackage-swapping"></a>Otomatik çözüm tabanlı VSPackage takas
 **Kaynak denetim kategorisi altındaki** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **seçenekleri** iletişim kutusundan El Ile kaynak denetimi VSPackages takas edebilirsiniz. Otomatik çözüm tabanlı paket değiştirme, belirli bir çözüm için belirlenmiş olan bir kaynak denetimi paketinin, bu çözüm açıldığında otomatik olarak etkin olarak ayarlandığı anlamına gelir. Her kaynak denetim paketi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> uygulamalıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], hem kaynak denetimi eklentileri (kaynak denetimi eklentisi API 'sini uygulama) hem de kaynak denetimi VSPackages arasındaki anahtarı işler.

 Kaynak denetim bağdaştırıcısı paketi herhangi bir kaynak denetimi eklentisi API tabanlı eklentiye geçiş yapmak için kullanılır. Ara kaynak denetim bağdaştırıcısı paketini değiştirme ve hangi kaynak denetimi eklentisinin etkin veya devre dışı olarak ayarlanması gerektiğini belirleme işlemi kullanıcı için saydamdır. Herhangi bir kaynak denetimi eklentisi etkin olduğunda bağdaştırıcı paketi her zaman etkindir. Yalnızca eklenti DLL 'sini yüklemek ve kaldırmak için iki kaynak denetimi eklentisi miktarı arasında geçiş yapın. Ancak, bir kaynak denetimi VSPackage 'a geçiş yapmak, uygun VSPackage 'ı yüklemek için IDE ile etkileşimde bulunmayı içerir.

 Herhangi bir çözüm açıldığında ve VSPackage için kayıt defteri anahtarı çözüm dosyasında olduğunda, bir kaynak denetimi VSPackage çağrılır. Çözüm açıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kayıt defteri değerini bulur ve uygun kaynak denetimi VSPackage 'ı yükler. Tüm kaynak denetimi VSPackages, yukarıda açıklanan kayıt defteri girişlerine sahip olmalıdır. Kaynak denetimi altındaki bir çözüm, belirli bir kaynak denetimi VSPackage ile ilişkili olarak işaretlenir. Kaynak denetimi VSPackages, otomatik çözüm tabanlı VSPackage takas özelliğini etkinleştirmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> uygulamalıdır.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Paket seçme ve değiştirme için Visual Studio Kullanıcı arabirimi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **, kaynak denetimi kategorisi altındaki** **Seçenekler** Iletişim kutusunda VSPackage ve eklenti seçimi için bir kullanıcı arabirimi sağlar. Kullanıcının etkin kaynak denetimi eklentisini veya VSPackage seçmesini sağlar. Açılan liste şunları içerir:

- Tüm yüklü kaynak denetimi paketleri

- Tüm yüklü kaynak denetimi eklentileri

- Kaynak kodu denetimini devre dışı bırakan bir "none" seçeneği

  Yalnızca etkin kaynak denetimi seçeneği için Kullanıcı arabirimi görünür. VSPackage seçimi, önceki VSPackage için Kullanıcı arabirimini gizler ve yeni bir kullanıcı arabirimi gösterir. Etkin VSPackage, Kullanıcı başına temelinde seçilir. Bir kullanıcının eşzamanlı olarak birden çok [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kopyası varsa, her biri farklı bir etkin VSPackage kullanabilir. Aynı bilgisayarda birden çok kullanıcı oturum açarsa, her bir kullanıcı farklı bir etkin VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açık olan ayrı örneklerine sahip olabilir. @No__t_0 birden çok örneği bir kullanıcı tarafından kapatıldığında, son açık çözüm için etkin olan kaynak denetimi VSPackage varsayılan kaynak denetimi VSPackage, yeniden başlatma sırasında etkin olarak ayarlanır.

  Önceki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümlerinden farklı olarak, IDE yeniden başlatması artık kaynak denetimi VSPackages ' ı geçmenin tek yoludur. VSPackage seçimi otomatiktir. Paketlerin değiştirilmesi için Windows kullanıcı ayrıcalıkları gerekir (yönetici veya Uzman Kullanıcı değil).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackage’lar](../../extensibility/internals/vspackages.md)