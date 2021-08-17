---
title: Kayıt ve seçim (kaynak denetimi VSPackage) | Microsoft Docs
description: kaynak denetimi vspackage 'ı Visual Studio kaydetme ve birden çok kayıtlı kaynak denetimi paketinden hangi paketin yükleneceğini seçme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3b2c64584eb550aba9bc0ea6240fccdeed79bb614001ca62235fface5d3635f9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275274"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Kayıt ve Seçim (Kaynak Denetimi VSPackage’ı)
Kaynak denetimi VSPackage, içinde kullanıma sunmak için kaydedilmelidir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Birden fazla kaynak denetimi VSPackage kayıtlıysa, Kullanıcı hangi VSPackage 'ın uygun zamanlarda yükleneceğini seçebilir. VSPackages hakkında daha fazla ayrıntı ve bunların nasıl kaydedileceği hakkında bilgi için bkz. [VSPackages](../../extensibility/internals/vspackages.md) .

## <a name="registering-a-source-control-package"></a>Kaynak denetim paketini kaydetme
 Kaynak denetim paketi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortamın onu bulabileceği ve desteklenen özelliklerini sorgulayabilmesi için kaydedilir. Bu, bir paket örneğinin yalnızca özellikleri veya komutları gerekli olduğunda ya da açıkça istendiği zaman oluşturulduğu bir gecikme yükleme şemasına göre yapılır.

 VSPackages, bilgileri sürüme özgü bir kayıt defteri anahtarına HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. Y*, burada *x* büyük sürüm numarası ve *Y* ise ikincil sürüm numarasıdır. Bu uygulama, uygulamasının birden çok sürümünü yan yana yüklemeyi destekleme yeteneği sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kullanıcı arabirimi (UI), birden fazla yüklü kaynak denetimi eklentisi arasından (kaynak denetim bağdaştırıcısı paketi aracılığıyla) seçim yapın ve kaynak denetimi VSPackages 'yi destekler. Tek seferde yalnızca bir etkin kaynak denetimi eklentisi veya VSPackage olabilir. Bununla birlikte, aşağıda açıklandığı gibi IDE, otomatik çözüm tabanlı bir paket değiştirme mekanizması aracılığıyla kaynak denetimi eklentileri ve VSPackages arasında geçiş yapılmasına izin verir. Bu seçim mekanizmasını etkinleştirmek için VSPackage kaynak denetiminin bölümünde bazı gereksinimler vardır.

### <a name="registry-entries"></a>Kayıt defteri girdileri
 Kaynak denetim paketinde üç özel GUID gerekir:

- Paket GUID 'SI: Bu, kaynak denetim uygulamasını (Bu bölümde ID_Package denir) içeren paket için ana GUID 'dir.

- kaynak denetimi guıd 'si: bu, Visual Studio kaynak denetimi saplamaya kaydolmak için kullanılan vspackage için bir guıd 'dir ve ayrıca bir komut uı bağlamı guıd 'si olarak da kullanılır. Kaynak denetimi hizmeti GUID 'SI, kaynak denetimi GUID 'sinin altına kaydedilir. Örnekte, kaynak denetimi GUID 'SI ID_SccProvider olarak adlandırılır.

- kaynak denetimi hizmeti guıd 'si: bu, Visual Studio tarafından kullanılan özel hizmet guıd 'sidir (bu bölümde SID_SccPkgService olarak adlandırılır). Buna ek olarak, kaynak denetimi paketinin VSPackages, araç pencereleri vb. için diğer GUID 'Leri tanımlanması gerekir.

  Aşağıdaki kayıt defteri girdilerinin bir kaynak denetimi VSPackage tarafından yapılması gerekir:

| Anahtar adı | Girişleriyle |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (varsayılan) = rg_sz: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (varsayılan) = rg_sz:\<Friendly name of Package><br /><br /> Hizmet = rg_sz: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (varsayılan) = rg_sz: #\<Resource ID for localized name><br /><br /> Paket = rg_sz: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Anahtar adının, `SourceCodeControl` tarafından zaten kullanıldığını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve için seçim olarak kullanılamaz olduğunu unutmayın \<PackageName> .) | (varsayılan) = rg_sz: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Kaynak denetim paketi seçme
 Çeşitli kaynak denetimi eklentisi API tabanlı eklentiler ve kaynak denetimi VSPackages, eşzamanlı olarak kaydedilmiş olabilir. Bir kaynak denetimi eklentisi veya VSPackage seçme işlemi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentiyi veya VSPackage 'ı uygun zamana yüklediğinizden emin olmalıdır ve gerekene kadar gereksiz bileşenleri yüklemeyi erteleyebilirsiniz. Ayrıca, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menü öğeleri, iletişim kutuları ve araç çubukları dahil, etkin olmayan diğer VSPackages öğelerinden tüm Kullanıcı arabirimini kaldırması ve etkin VSPackage için Kullanıcı arabirimini görüntülemesi gerekir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aşağıdaki işlemlerden herhangi biri gerçekleştirildiğinde bir kaynak denetimi VSPackage yükler:

- Çözüm açıldı (çözüm kaynak denetimi altında olduğunda).

   Kaynak denetimi altındaki bir çözüm veya proje açıldığında, IDE, bu çözüm için ayrılmış kaynak denetimi VSPackage 'ın yüklenmesine neden olur.

- VSPackage kaynak denetiminin herhangi bir menü komutu yürütülür.

  Kaynak denetimi VSPackage, ihtiyaç duydukları tüm bileşenleri yalnızca gerçekten kullanılacaksa (yani Gecikmeli yükleme olarak bilinir) yüklemesi gerekir.

### <a name="automatic-solution-based-vspackage-swapping"></a>Otomatik çözüm tabanlı VSPackage takas
 Kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kategorisi altındaki **Seçenekler** iletişim kutusundan, kaynak denetimi VSPackages 'leri el ile  takas edebilirsiniz. Otomatik çözüm tabanlı paket değiştirme, belirli bir çözüm için belirlenmiş olan bir kaynak denetimi paketinin, bu çözüm açıldığında otomatik olarak etkin olarak ayarlandığı anlamına gelir. Her kaynak denetim paketinin ve uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kaynak denetimi eklentileri (kaynak denetimi eklentisi API 'sini uygulama) ve kaynak denetimi VSPackages arasındaki anahtarı işler.

 Kaynak denetim bağdaştırıcısı paketi herhangi bir kaynak denetimi eklentisi API tabanlı eklentiye geçiş yapmak için kullanılır. Ara kaynak denetim bağdaştırıcısı paketini değiştirme ve hangi kaynak denetimi eklentisinin etkin veya devre dışı olarak ayarlanması gerektiğini belirleme işlemi kullanıcı için saydamdır. Herhangi bir kaynak denetimi eklentisi etkin olduğunda bağdaştırıcı paketi her zaman etkindir. Yalnızca eklenti DLL 'sini yüklemek ve kaldırmak için iki kaynak denetimi eklentisi miktarı arasında geçiş yapın. Ancak, bir kaynak denetimi VSPackage 'a geçiş yapmak, uygun VSPackage 'ı yüklemek için IDE ile etkileşimde bulunmayı içerir.

 Herhangi bir çözüm açıldığında ve VSPackage için kayıt defteri anahtarı çözüm dosyasında olduğunda, bir kaynak denetimi VSPackage çağrılır. Çözüm açıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kayıt defteri değerini bulur ve uygun kaynak denetimi VSPackage 'ı yükler. Tüm kaynak denetimi VSPackages, yukarıda açıklanan kayıt defteri girişlerine sahip olmalıdır. Kaynak denetimi altındaki bir çözüm, belirli bir kaynak denetimi VSPackage ile ilişkili olarak işaretlenir. Kaynak denetimi VSPackages, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> otomatik çözüm tabanlı VSPackage değiştirmeyi etkinleştirmek için öğesini uygulamalıdır.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio Paket seçme ve değiştirme için Kullanıcı arabirimi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**kaynak denetim kategorisi altındaki** **Seçenekler** iletişim kutusunda yer alan kaynak denetimi VSPackage ve eklenti seçimi için bir kullanıcı arabirimi sağlar. Kullanıcının etkin kaynak denetimi eklentisini veya VSPackage seçmesini sağlar. Açılan liste şunları içerir:

- Tüm yüklü kaynak denetimi paketleri

- Tüm yüklü kaynak denetimi eklentileri

- Kaynak kodu denetimini devre dışı bırakan bir "none" seçeneği

  Yalnızca etkin kaynak denetimi seçeneği için Kullanıcı arabirimi görünür. VSPackage seçimi, önceki VSPackage için Kullanıcı arabirimini gizler ve yeni bir kullanıcı arabirimi gösterir. Etkin VSPackage, Kullanıcı başına temelinde seçilir. Bir kullanıcının eşzamanlı olarak birden fazla kopyası varsa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , her biri farklı bir etkin VSPackage kullanabilir. Aynı bilgisayarda birden çok kullanıcı oturum açarsa, her Kullanıcı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] farklı bir etkin VSPackage ile ayrı ayrı açık olabilir. Birden çok örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir kullanıcı tarafından kapatıldığında, son açık çözüm için etkin olan VSPackage kaynak denetimi, yeniden başlatma sırasında etkin olarak ayarlanacak varsayılan kaynak denetimi VSPackage olur.

  Önceki sürümlerinden farklı olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , IDE yeniden başlatması artık kaynak denetimi VSPackages ' ı geçmenin tek yoludur. VSPackage seçimi otomatiktir. paket değiştirme Windows kullanıcı ayrıcalıkları gerektirir (yönetici veya uzman kullanıcı değil).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
