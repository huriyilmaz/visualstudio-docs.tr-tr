---
title: Kayıt ve seçim (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 692f2a9f34edd41839179f7229e079ec8e791800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185827"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Kayıt ve Seçim (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi VSPackage, içinde kullanıma sunmak için kaydedilmelidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Birden fazla kaynak denetimi VSPackage kayıtlıysa, Kullanıcı hangi VSPackage 'ın uygun zamanlarda yükleneceğini seçebilir. VSPackages hakkında daha fazla ayrıntı ve bunların nasıl kaydedileceği hakkında bilgi için bkz. [VSPackages](../../extensibility/internals/vspackages.md) .  
  
## <a name="registering-a-source-control-package"></a>Kaynak denetim paketini kaydetme  
 Kaynak denetim paketi, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ortamın onu bulabileceği ve desteklenen özelliklerini sorgulayabilmesi için kaydedilir. Bu, bir paket örneğinin yalnızca özellikleri veya komutları gerekli olduğunda ya da açıkça istendiği zaman oluşturulduğu bir gecikme yükleme şemasına göre yapılır.  
  
 VSPackages, bilgileri sürüme özgü bir kayıt defteri anahtarına, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *X. Y*' dir; burada *X* , ana sürüm numarası ve *Y* ise ikincil sürüm numarasıdır. Bu uygulama, uygulamasının birden çok sürümünü yan yana yüklemeyi destekleme yeteneği sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kullanıcı arabirimi (UI), birden fazla yüklü kaynak denetimi eklentisi arasından (kaynak denetim bağdaştırıcısı paketi aracılığıyla) seçim yapın ve kaynak denetimi VSPackages 'yi destekler. Tek seferde yalnızca bir etkin kaynak denetimi eklentisi veya VSPackage olabilir. Bununla birlikte, aşağıda açıklandığı gibi IDE, otomatik çözüm tabanlı bir paket değiştirme mekanizması aracılığıyla kaynak denetimi eklentileri ve VSPackages arasında geçiş yapılmasına izin verir. Bu seçim mekanizmasını etkinleştirmek için VSPackage kaynak denetiminin bölümünde bazı gereksinimler vardır.  
  
### <a name="registry-entries"></a>Kayıt defteri girdileri  
 Kaynak denetim paketinde üç özel GUID gerekir:  
  
- Paket GUID 'SI: Bu, kaynak denetim uygulamasını (Bu bölümde ID_Package denir) içeren paket için ana GUID 'dir.  
  
- Kaynak denetimi GUID 'SI: Bu, Visual Studio kaynak denetimi saplamaya kaydolmak için kullanılan VSPackage için bir GUID 'dir ve ayrıca bir komut UI bağlamı GUID 'SI olarak da kullanılır. Kaynak denetimi hizmeti GUID 'SI, kaynak denetimi GUID 'sinin altına kaydedilir. Örnekte, kaynak denetimi GUID 'SI ID_SccProvider olarak adlandırılır.  
  
- Kaynak denetimi hizmeti GUID 'SI: Bu, Visual Studio tarafından kullanılan özel hizmet GUID 'sidir (Bu bölümde SID_SccPkgService denir). Buna ek olarak, kaynak denetimi paketinin VSPackages, araç pencereleri vb. için diğer GUID 'Leri tanımlanması gerekir.  
  
  Aşağıdaki kayıt defteri girdilerinin bir kaynak denetimi VSPackage tarafından yapılması gerekir:  
  
|Anahtar adı|Girişleriyle|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(varsayılan) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(varsayılan) = rg_sz:\<Friendly name of Package><br /><br /> Hizmet = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(varsayılan) = rg_sz: #\<Resource ID for localized name><br /><br /> Paket = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Anahtar adının, `SourceCodeControl` tarafından zaten kullanıldığını [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve için seçim olarak kullanılamaz olduğunu unutmayın \<PackageName> .)|(varsayılan) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Kaynak denetim paketi seçme  
 Çeşitli kaynak denetimi eklentisi API tabanlı eklentiler ve kaynak denetimi VSPackages, eşzamanlı olarak kaydedilmiş olabilir. Bir kaynak denetimi eklentisi veya VSPackage seçme işlemi, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eklentiyi veya VSPackage 'ı uygun zamana yüklediğinizden emin olmalıdır ve gerekene kadar gereksiz bileşenleri yüklemeyi erteleyebilirsiniz. Ayrıca, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menü öğeleri, iletişim kutuları ve araç çubukları dahil, etkin olmayan diğer VSPackages öğelerinden tüm Kullanıcı arabirimini kaldırması ve etkin VSPackage için Kullanıcı arabirimini görüntülemesi gerekir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Aşağıdaki işlemlerden herhangi biri gerçekleştirildiğinde bir kaynak denetimi VSPackage yükler:  
  
- Çözüm açıldı (çözüm kaynak denetimi altında olduğunda).  
  
   Kaynak denetimi altındaki bir çözüm veya proje açıldığında, IDE, bu çözüm için ayrılmış kaynak denetimi VSPackage 'ın yüklenmesine neden olur.  
  
- VSPackage kaynak denetiminin herhangi bir menü komutu yürütülür.  
  
  Kaynak denetimi VSPackage, ihtiyaç duydukları tüm bileşenleri yalnızca gerçekten kullanılacaksa (yani Gecikmeli yükleme olarak bilinir) yüklemesi gerekir.  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Otomatik çözüm tabanlı VSPackage takas  
 Kaynak denetimi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kategorisi altındaki **Seçenekler** iletişim kutusundan, kaynak denetimi VSPackages 'leri el ile **Source Control** takas edebilirsiniz. Otomatik çözüm tabanlı paket değiştirme, belirli bir çözüm için belirlenmiş olan bir kaynak denetimi paketinin, bu çözüm açıldığında otomatik olarak etkin olarak ayarlandığı anlamına gelir. Her kaynak denetim paketinin ve uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kaynak denetimi eklentileri (kaynak denetimi eklentisi API 'sini uygulama) ve kaynak denetimi VSPackages arasındaki anahtarı işler.  
  
 Kaynak denetim bağdaştırıcısı paketi herhangi bir kaynak denetimi eklentisi API tabanlı eklentiye geçiş yapmak için kullanılır. Ara kaynak denetim bağdaştırıcısı paketini değiştirme ve hangi kaynak denetimi eklentisinin etkin veya devre dışı olarak ayarlanması gerektiğini belirleme işlemi kullanıcı için saydamdır. Herhangi bir kaynak denetimi eklentisi etkin olduğunda bağdaştırıcı paketi her zaman etkindir. Yalnızca eklenti DLL 'sini yüklemek ve kaldırmak için iki kaynak denetimi eklentisi miktarı arasında geçiş yapın. Ancak, bir kaynak denetimi VSPackage 'a geçiş yapmak, uygun VSPackage 'ı yüklemek için IDE ile etkileşimde bulunmayı içerir.  
  
 Herhangi bir çözüm açıldığında ve VSPackage için kayıt defteri anahtarı çözüm dosyasında olduğunda, bir kaynak denetimi VSPackage çağrılır. Çözüm açıldığında, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kayıt defteri değerini bulur ve uygun kaynak denetimi VSPackage 'ı yükler. Tüm kaynak denetimi VSPackages, yukarıda açıklanan kayıt defteri girişlerine sahip olmalıdır. Kaynak denetimi altındaki bir çözüm, belirli bir kaynak denetimi VSPackage ile ilişkili olarak işaretlenir. Kaynak denetimi VSPackages, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> otomatik çözüm tabanlı VSPackage değiştirmeyi etkinleştirmek için öğesini uygulamalıdır.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Paket seçme ve değiştirme için Visual Studio Kullanıcı arabirimi  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]**kaynak denetim kategorisi altındaki** **Seçenekler** iletişim kutusunda yer alan kaynak denetimi VSPackage ve eklenti seçimi için bir kullanıcı arabirimi sağlar. Kullanıcının etkin kaynak denetimi eklentisini veya VSPackage seçmesini sağlar. Açılan liste şunları içerir:  
  
- Tüm yüklü kaynak denetimi paketleri  
  
- Tüm yüklü kaynak denetimi eklentileri  
  
- Kaynak kodu denetimini devre dışı bırakan bir "none" seçeneği  
  
  Yalnızca etkin kaynak denetimi seçeneği için Kullanıcı arabirimi görünür. VSPackage seçimi, önceki VSPackage için Kullanıcı arabirimini gizler ve yeni bir kullanıcı arabirimi gösterir. Etkin VSPackage, Kullanıcı başına temelinde seçilir. Bir kullanıcının eşzamanlı olarak birden fazla kopyası varsa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , her biri farklı bir etkin VSPackage kullanabilir. Aynı bilgisayarda birden çok kullanıcı oturum açarsa, her Kullanıcı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] farklı bir etkin VSPackage ile ayrı ayrı açık olabilir. Birden çok örneği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir kullanıcı tarafından kapatıldığında, son açık çözüm için etkin olan VSPackage kaynak denetimi, yeniden başlatma sırasında etkin olarak ayarlanacak varsayılan kaynak denetimi VSPackage olur.  
  
  Önceki sürümlerinden farklı olarak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , IDE yeniden başlatması artık kaynak denetimi VSPackages ' ı geçmenin tek yoludur. VSPackage seçimi otomatiktir. Paketlerin değiştirilmesi için Windows kullanıcı ayrıcalıkları gerekir (yönetici veya Uzman Kullanıcı değil).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Özelliklerinde](../../extensibility/internals/source-control-vspackage-features.md)   
 [Kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackage’lar](../../extensibility/internals/vspackages.md)
