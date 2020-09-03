---
title: Bağlantı görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 930cec012bfda49c61116ada2ba6df10c3a48f51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850993"
---
# <a name="link-task"></a>Bağlantı Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++ bağlayıcı aracını sarmalanmış link.exe. Bağlayıcı aracı ortak nesne dosyası biçimi (COFF) nesne dosyalarını ve kitaplıklarını, yürütülebilir (. exe) dosya veya dinamik bağlantı kitaplığı (DLL) oluşturmak için bağlar. Daha fazla bilgi için bkz. [bağlayıcı seçenekleri](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda **bağlantı** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.  
  
- **AdditionalDependencies**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Komuta eklenecek giriş dosyalarının bir listesini belirtir.  
  
   Daha fazla bilgi için bkz. [giriş dosyalarını bağlama](https://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **Additionallibrarydizinler**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Ortam kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.  
  
   Daha fazla bilgi için bkz. [/LIBPATH (ek libpath)](https://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   `dependency`Bildirim dosyasının bölümüne yerleştirilecek öznitelikleri belirtir.  
  
   Daha fazla bilgi için bkz. [/Manifestdependency (Bildirim Bağımlılıklarını Belirt)](https://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Ayrıca, [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Yayımcı yapılandırma dosyaları" bölümüne bakın.  
  
- **AdditionalOptions**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Komut satırında belirtilen bağlayıcı seçeneklerinin bir listesi. Örneğin, **"**_/option1/option2/option #_". Başka bir **bağlantı** görevi parametresi tarafından temsil edilmeyen bağlayıcı seçeneklerini belirtmek için bu parametreyi kullanın.  
  
   Daha fazla bilgi için bkz. [bağlayıcı seçenekleri](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Bir derlemeye modül başvurusu ekler.  
  
   Daha fazla bilgi için bkz. [/ASSEMBLYMODULE (DERLEMEYE MSIL Modülü ekleme)](https://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **ALLOWISOLATION**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , işletim sisteminin bildirim aramalarını ve yüklemelerini yapmasına neden olur. İse `false` , dll 'lerin bir bildirim olmadığı gibi yüklendiğini belirtir.  
  
   Daha fazla bilgi için bkz. [/ALLOWISOLATION (bildirim arama)](https://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`Hata ayıklayıcı, hata ayıklama bilgileri izleme ile birlikte hata ayıklamış **ggableattribute** ÖZNITELIĞINI yayar ve JIT iyileştirmeleri devre dışı bırakır Eğer `false` , hata ayıklayıcı **ggableattribute** özniteliğini yayar, ancak hata ayıklama bilgileri izlemeyi devre DıŞı bırakır ve JIT iyileştirmelerini mümkün  
  
   Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (hata ayıklama Ggableattribute Ekle)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **ASSEMBLYLINKRESOURCE**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Kaynağın adını belirtin.  
  
   Daha fazla bilgi için bkz. [/Assemblylinkresource (.NET Framework kaynağına bağlantı)](https://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Örtük **Boolean** parametresi.  
  
   Daha derin dosya izlemenin bağlantı artımlı davranışını yakalamasını sağlar. Her zaman `true` döndürür.  
  
- **BaseAddress**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Oluşturulan program veya DLL için bir temel adres ayarlar. `{address[,size] | @filename,key}` belirtin.  
  
   Daha fazla bilgi için bkz. [/Base (temel adres)](https://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **Buildingınıde**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   True ise, MSBuild 'in IDE 'den çağrıldığı anlamına gelir. Aksi takdirde, MSBuild 'in komut satırından çağrıldığını gösterir.  
  
   Bu parametrenin denk bağlayıcı seçeneği yok.  
  
- **CLRIMAGETYPE**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Ortak dil çalışma zamanı (CLR) görüntüsünün türünü ayarlar.  
  
   Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılanını** - *\<none>*  
  
  - **ForceIJWImage**  -  **/Clrimagetype: IJW**  
  
  - **Forcepureilımage**  -  **/Clrimagetype: saf**  
  
  - **Forcesafeılımage**  -  **/Clrimagetype: güvenli**  
  
    Daha fazla bilgi için bkz. [/Clrimagetype (clr görüntü türünü belirt)](https://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSUPPORTLASTERROR 'ü**  
  
   İsteğe bağlı **dize** parametresi.  
  
   P/Invoke mekanizması aracılığıyla çağrılan işlevlerin son hata kodunu korur.  
  
   Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Etkin**  -  **/CLRSupportLastError**  
  
  - **Devre dışı**  -  **/CLRSupportLastError: Hayır**  
  
  - **Sistem dll 'leri**  -  **/CLRSupportLastError: SYSTEMDLL**  
  
    Daha fazla bilgi için bkz. [/CLRSUPPORTLASTERROR (PInvoke çağrıları Için son hata kodunu koru)](https://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRTHREADATTRIBUTE**  
  
   İsteğe bağlı **dize** parametresi.  
  
   CLR programınızın giriş noktası için iş parçacığı oluşturma özniteliğini açıkça belirtir.  
  
   Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Defaultthreadingattribute**  -  **/CLRTHREADATTRIBUTE: yok**  
  
  - **Mtathreadingattribute**  -  **/CLRTHREADATTRIBUTE: MTA**  
  
  - **Stathreadingattribute**  -  **/CLRTHREADATTRIBUTE: STA**  
  
    Daha fazla bilgi için bkz. [/CLRTHREADATTRIBUTE (clr Iş parçacığı özniteliğini ayarlama)](https://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   Bağlayıcının **SuppressUnmanagedCodeSecurityAttribute** ' i yönetilen koddan yerel dll 'lere bağlayıcı tarafından oluşturulan P/Invoke çağrılarına uygulayıp uygulayamayacağını belirtir.  
  
   Daha fazla bilgi için bkz. [/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute ekleyin)](https://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **Createhotpatchableımage**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Sık yama için bir görüntü hazırlar.  
  
   Bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Etkin**  -  **/Functionpadmin**  
  
  - **X86Image**  -  **/Functionpadmin: 5**  
  
  - **X64Image**  -  **/Functionpadmin: 6**  
  
  - **Itaniumımage**  -  **/Functionpadmin: 16**  
  
    Daha fazla bilgi için bkz. [/functionpadmin (düzeltme eki eklenebilir görüntü oluşturma)](https://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **Dataexecutionengellemesini**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`, Bir yürütülebilir dosyanın Windows Veri Yürütme Engellemesi özelliği ile uyumlu olacak şekilde sınanmış olduğunu gösterir.  
  
   Daha fazla bilgi için bkz. [/NXCOMPAT (veri yürütme engellemesi Ile uyumlu)](https://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Bu parametre, dll 'lerin *gecikmeli yüklenmesine* neden olur. Yük gecikmesi için DLL 'nin adını belirtin.  
  
   Daha fazla bilgi için bkz. [/delayload (Gecikmeli yük Içeri aktarma)](https://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   Eğer `true` , bir derlemeyi kısmen imzalar. Varsayılan değer `false` şeklindedir.  
  
   Daha fazla bilgi için bkz. [/delaysign (derlemeyi kısmen imzala)](https://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Sürücü**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Windows NT Çekirdek modu sürücüsü oluşturmak için bu parametreyi belirtin.  
  
   Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<none>*  
  
  - **Sürücü**  -  **/DRIVER**  
  
  - **Yalnızca yukarı**  -  **/DRIVER: yalnızca yukarı**  
  
  - **WDM**  -  **/DRIVER: WDM**  
  
    Daha fazla bilgi için bkz. [/Driver (WINDOWS NT Çekirdek modu sürücüsü)](https://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Bir derlemeye kaynak dosyası katıştırır. Gerekli kaynak dosya adını belirtin. İsteğe bağlı olarak, kaynağı yüklemek için kullanılan mantıksal adı ve kaynak dosyasının özel olduğunu derleme bildiriminde belirten **özel** seçeneğini belirtin.  
  
   Daha fazla bilgi için bkz. [/ASSEMBLYRESOURCE (yönetilen kaynağı katıştır)](https://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **Enablecomdatkatlamalı**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   Varsa `true` , aynı COMDAT katlamayı mümkün bir şekilde sunar.  
  
   Daha fazla bilgi için bkz `ICF[= iterations]` . [/opt (iyileştirmeler)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac)bağımsız değişkeni.  
  
- **EnableUAC**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , Kullanıcı hesabı denetimi (UAC) bilgisinin program bildirimine gömülü olduğunu belirtir.  
  
   Daha fazla bilgi için bkz. [/bildirimini estuac (BILDIRIMDEKI UAC bilgilerini katıştırır)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir. exe dosyası veya DLL için başlangıç adresi olarak bir giriş noktası işlevi belirtir. Parametre değeri olarak bir işlev adı belirtin.  
  
   Daha fazla bilgi için bkz. [/Entry (giriş noktası simgesi)](https://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , yalnızca tercih edilen temel adresinde yüklenebilen bir program veya dll oluşturur.  
  
   Daha fazla bilgi için bkz. [/Fixed (sabit temel adres)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bağlayıcıya bir sembol başvuruluyorsa ancak tanımlanmasa bile geçerli bir. exe dosyası veya DLL oluşturmasını söyler veya çarpma tanımlanmış olarak tanımlanır.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Etkin**  -  **/Force**  
  
  - Yalnızca Çoğullydefinedsymbol **MultiplyDefinedSymbolOnly**  -  **/Force: bırden çok**  
  
  - Yalnızca Undefinedsymbol **UndefinedSymbolOnly**  -  **/Force: çözümlenmemiş**  
  
    Daha fazla bilgi için bkz. [/Force (Dosya çıktısını zorla)](https://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **Forcesyımbolreferences**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Bu parametre, bağlayıcının sembol tablosuna belirtilen bir sembol eklemesini söyler.  
  
   Daha fazla bilgi için bkz. [/Include (simge başvurularını zorla)](https://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bu parametre, belirtilen paketlenmiş işlevleri (Comtts) görüntüye önceden belirlenmiş bir sırada yerleştirerek programınızı iyileştirir.  
  
   Daha fazla bilgi için bkz. [/Order (Işlevleri sırayla yerleştirme)](https://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` ,. exe dosyası veya dll için hata ayıklama bilgileri oluşturur.  
  
   Daha fazla bilgi için bkz. [/Debug (hata ayıklama bilgisi oluştur)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , yan yana bildirim dosyası oluşturur.  
  
   Daha fazla bilgi için bkz. [/manifest (yan yana derleme bildirimi oluşturma)](https://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bir *eşleme dosyası*oluşturur. Eşleme dosyasının dosya adı uzantısı. map ' dir.  
  
   Daha fazla bilgi için bkz. [/Map (mapfile üret)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Yığın üzerinde aynı anda ayrılacak fiziksel bellek miktarını belirtir.  
  
   Daha fazla bilgi için bkz `commit` ./Heap içindeki bağımsız değişken [(yığın boyutunu ayarlama)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Ayrıca bkz. **Heaprezervesize** parametresi.  
  
- **Heaprezervesize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Sanal bellekteki toplam yığın ayırmayı belirtir.  
  
   Daha fazla bilgi için bkz `reserve` ./Heap içindeki bağımsız değişken [(yığın boyutunu ayarlama)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Ayrıca bkz. bu tablodaki **HeapCommitSize** parametresi.  
  
- **IgnoreAllDefaultLibraries**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bağlayıcının bir veya daha fazla varsayılan kitaplığı dış başvuruları çözümlediğinde aradığı kitaplık listesinden kaldırmasını söyler.  
  
   Daha fazla bilgi için bkz. [/nodefaultlib (kitaplıkları Yoksay)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , kaynak kodundaki tüm IDL özniteliklerinin bir. IDL dosyasına işlenmediğini belirtir.  
  
   Daha fazla bilgi için bkz. [/IGNOREIDL (öznitelikleri MIDL 'ye işleme)](https://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`Bu yapılandırma tarafından oluşturulan içeri aktarma kitaplığının bağımlı projelere aktarılmaması gerektiğini belirtir.  
  
   Bu parametre bir bağlayıcı seçeneğine karşılık gelmiyor.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Yoksayılacak bir veya daha fazla varsayılan kitaplık adını belirtir. Noktalı virgülle ayırarak birden çok kitaplığı ayırın.  
  
   Daha fazla bilgi için bkz. [/nodefaultlib (kitaplıkları Yoksay)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **Imagehassafeexceptionhandlers**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   Varsa `true` , bağlayıcı yalnızca görüntünün güvenli özel durum işleyicilerinin bir tablosunu da üretebilir bir görüntü oluşturur.  
  
   Daha fazla bilgi için bkz. [/SafeSEH (görüntü güvenli özel durum işleyicilerine sahiptir)](https://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Varsayılan kitaplık adının yerini alan, Kullanıcı tarafından belirtilen bir içeri aktarma kitaplığı adı.  
  
   Daha fazla bilgi için bkz. [/ımplib (ad Içeri aktarma kitaplığı)](https://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İmzalı bir derleme için anahtarı içeren kapsayıcı.  
  
   Daha fazla bilgi için bkz. [/keycontainer (bir derlemeyi imzalamak için bir anahtar kapsayıcısı belirtin)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Ayrıca bkz. bu tablodaki **keyfile** parametresi.  
  
- **Dosyasına**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İmzalı bir derleme için anahtarı içeren bir dosyayı belirtir.  
  
   Daha fazla bilgi için bkz. [/keyfile (bir derlemeyi imzalamak Için anahtar veya anahtar çiftini belirtin)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Ayrıca, bkz. **keycontainer** parametresi.  
  
- **LargeAddressAware**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`Uygulama, 2 gigabayt 'tan daha büyük adresleri işleyebilir.  
  
   Daha fazla bilgi için bkz. [/LARGEADDRESSAWARE (büyük adresleri işleme)](https://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , ana çıkış dosyası olarak BIR DLL oluşturur.  
  
   Daha fazla bilgi için bkz. [/dll (dll derleme)](https://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İç derleyici hatası (ıCE) bilgilerini doğrudan Microsoft 'a sağlamanıza olanak tanır.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Noerrorreport**  -  **/errorreport: yok**  
  
  - **Hemen sor**  -  **/errorreport: Prompt**  
  
  - **Queuefornextlogin**  -  **/errorreport: kuyruk**  
  
  - **Senderrorreport**  -  **/errorreport: gönder**  
  
    Daha fazla bilgi için bkz. [/errorreport (Iç bağlayıcı hatalarını raporla)](https://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **Linkıncreıncre**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , artımlı bağlamayı mümkün.  
  
   Daha fazla bilgi için bkz. [/ıncreıncre(artımlı bağlantı)](https://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , proje bağımlılıklarından kitaplık çıktılarının otomatik olarak bağlandığını belirtir.  
  
   Bu parametre bir bağlayıcı seçeneğine karşılık gelmiyor.  
  
- **Bağlantı durumu**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bağlayıcının bağlantının yüzdesini gösteren bir ilerleme göstergesi görüntüleneceğini belirtir.  
  
   Daha fazla bilgi için `STATUS` [/LTCG (bağlama zamanı kodu oluşturma)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2)bağımsız değişkenine bakın.  
  
- **LinkTimeCodeGeneration**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Profil temelli iyileştirme seçeneklerini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılanını** - *\<none>*  
  
  - **Uselinktimecodegeneration**  -  **/LTCG**  
  
  - **PGINSTRUMENT**  -  **/LTCG: PGINSTRUMENT**  
  
  - **Pgoptimization**  -  **/LTCG: PGOptimize**  
  
  - **PGUpdate**  
  
     \-**/LTCG: PGUpdate**  
  
    Daha fazla bilgi için bkz. [/LTCG (bağlama zamanı kodu oluşturma)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **MANIFESTFILE**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan bildirim dosyası adını belirtilen dosya adı olarak değiştirir.  
  
   Daha fazla bilgi için bkz. [/ManifestFile (ad bildirim dosyası)](https://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **Mapdışarı aktarmalar**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bağlayıcının bir eşleme dosyasına aktarılmış işlevleri içermesini söyler.  
  
   Daha fazla bilgi için bkz `EXPORTS` . [/MapInfo bağımsız değişkeni (mapfile Içinde bilgi ekleme)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan eşleme dosyası adını belirtilen dosya adıyla değiştirir.  
  
- **MergedIDLBaseFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   . IDL dosyasının dosya adı ve dosya adı uzantısını belirtir.  
  
   Daha fazla bilgi için bkz. [/IDLOUT (MıDL çıktı dosyalarını Adlandır)](https://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir görüntüdeki bölümleri birleştirir. `from-section=to-section` belirtin.  
  
   Daha fazla bilgi için bkz. [/merge (bölümleri birleştirme)](https://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **Mıdlcommandfile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   MıDL komut satırı seçeneklerini içeren bir dosyanın adını belirtin.  
  
   Daha fazla bilgi için bkz. [/MIDL (MIDL komut satırı seçeneklerini belirtin)](https://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Alt sistemin gerekli en düşük sürümünü belirtir. Bağımsız değişkenler 0 ile 65535 aralığındaki ondalık sayılardır.  
  
- **ModuleDefinitionFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   [Modül tanım dosyasının](https://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8)adını belirtir.  
  
   Daha fazla bilgi için bkz. [/def (modül tanım dosyasını belirt)](https://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Belirtilen MS-DOS saplama programını bir Win32 programına iliştirir.  
  
   Daha fazla bilgi için bkz. [/stub (MS-DOS saplama dosyası adı)](https://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` yalnızca kaynak dll 'i belirtir.  
  
   Daha fazla bilgi için bkz. [/NOENTRY (giriş noktası yok)](https://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Örtük **dize []** parametresi.  
  
   Bağlı nesne dosyalarını belirtir.  
  
- **OptimizeReferences**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , hiçbir şekilde başvurulmayan işlevleri ve/veya verileri ortadan kaldırır.  
  
   Daha fazla bilgi için bkz `REF` . [/opt (iyileştirmeler)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac)içindeki bağımsız değişken.  
  
- **Çıktı**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bağlayıcının oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.  
  
   Daha fazla bilgi için bkz. [/Out (çıktı dosyası adı)](https://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`Çıktıyı kaydet etkinse, kayıt defteri yazmaları **HKEY_CLASSES_ROOT** **HKEY_CURRENT_USER**yeniden yönlendirilmeye zorlar.  
  
- **PreprocessOutput**  
  
   İsteğe bağlı `ITaskItem[]` parametre.  
  
   Görevler tarafından tüketilen ve yayılan bir Önişlemci çıkış öğeleri dizisi tanımlar.  
  
- **PreventDllBinding**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bağlı resmin bağlı olmaması gerektiğini Bind.exe gösterir.  
  
   Daha fazla bilgi için bkz. [/Allowbind (dll bağlamasını engelle)](https://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profil**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , **performans araçları** Profilcisi ile kullanılabilecek bir çıkış dosyası üretir.  
  
   Daha fazla bilgi için bkz. [/profile (performans araçları profil Oluşturucu)](https://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **Profilekılavuz Ddatabase**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Çalışan programla ilgili bilgileri tutmak için kullanılacak. pgd dosyasının adını belirtir  
  
   Daha fazla bilgi için bkz. [/PGD (Profil temelli iyileştirmeler Için veritabanını belirt)](https://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bağlayıcının oluşturduğu program veritabanı (PDB) için bir ad belirtir.  
  
   Daha fazla bilgi için bkz. [/pdb (program veritabanını kullan)](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`, Windows 'un *Adres alanı düzeni rastgele seçme* (ASLR) özelliğini kullanarak yükleme zamanında rastgele bir şekilde yeniden temel alan yürütülebilir bir görüntü oluşturur.  
  
   Daha fazla bilgi için bkz. [/DynamicBase (adres boşluğu düzeni rastgele seçimini kullan)](https://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bu derleme için birincil çıktıyı kaydeder.  
  
- **Sectionhizalaması**  
  
   İsteğe bağlı **tamsayı** parametresi.  
  
   Programın doğrusal adres alanındaki her bölümün hizalamasını belirtir. Parametre değeri bir birim bayt sayısıdır ve ikinin gücünden oluşur.  
  
   Daha fazla bilgi için bkz. [/align (Bölüm hizalaması)](https://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bir. exe dosyasının üst bilgisindeki sağlama toplamını ayarlar.  
  
   Daha fazla bilgi için bkz. [/Release (sağlama toplamını ayarla)](https://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bağlama işlemi için ilerleme raporlarının ayrıntı düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<none>*  
  
  - **Linkverbose**  -  **/Verbose**  
  
  - **LinkVerboseLib**  -  **/Verbose: lib**  
  
  - **LinkVerboseICF**  -  **/verbose: ICF**  
  
  - **LinkVerboseREF**  -  **/verbose: ref**  
  
  - **LinkVerboseSAFESEH**  -  **/verbose: SafeSEH**  
  
  - **LinkVerboseCLR**  -  **/verbose: clr**  
  
    Daha fazla bilgi için bkz. [/verbose (Ilerleme Iletilerini Yazdır)](https://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Kaynaklar**  
  
   Gerekli `ITaskItem[]` parametre.  
  
   Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.  
  
- **Belirtilen Yılözniteliklerini**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Bir bölümün özniteliklerini belirtir. Bu, bölüm için. obj dosyası derlendiğinde ayarlanan öznitelikleri geçersiz kılar.  
  
   Daha fazla bilgi için bkz. [/section (bölüm özniteliklerini belirt)](https://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Ek bellek tahsis edildiğinde her bir ayırdaki fiziksel bellek miktarını belirtir.  
  
   Daha fazla bilgi için bkz `commit` . [/Stack (yığın ayırmaları)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c)bağımsız değişkeni.  
  
- **Stackrezervesize**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Sanal bellekteki toplam yığın ayırma boyutunu belirtir.  
  
   Daha fazla bilgi için bkz `reserve` . [/Stack (yığın ayırmaları)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c)bağımsız değişkeni.  
  
- **StripPrivateSymbols**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Müşterilerinize dağıtmak istemediğiniz sembolleri atlatabilecek ikinci program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.  
  
   Daha fazla bilgi için bkz. [/Pdbçıkarıldı (özel sembolleri Strip)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **Sistemin**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Yürütülebilir dosyanın ortamını belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<none>*  
  
  - **Konsol**  -  **/Subsystem: Console**  
  
  - **Windows**  -  **/Subsystem: WINDOWS**  
  
  - **Yerel**  -  **/Subsystem: NATIVE**  
  
  - **EFI uygulaması**  -  **/Subsystem: EFI_APPLICATION**  
  
  - **EFI Önyükleme hizmeti sürücüsü**  -  **/Subsystem: EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFı ROM**  -  **/Subsystem: EFI_ROM**  
  
  - **EFI çalışma zamanı**  -  **/Subsystem: EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE**  -  **/Subsystem: WINDOWSCE**  
  
  - **POSIX**  -  **/Subsystem: POSIX**  
  
    Daha fazla bilgi için bkz. [/Subsystem (alt sistemi belirt)](https://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bağlayıcının son görüntüde bağlanabilir bir Içeri aktarma adres tablosu (ıAT) içermeyeceğini söyler.  
  
   Daha fazla bilgi için `NOBIND` [/Delay (yük Içeri aktarma ayarlarını geciktir)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c)bağımsız değişkenine bakın.  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , gecikme Yükleme Yardımcısı IŞLEVINE dll 'nin açıkça kaldırılmasını desteklediğini söyler.  
  
   Daha fazla bilgi için `UNLOAD` [/Delay (yük Içeri aktarma ayarlarını geciktir)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c)bağımsız değişkenine bakın.  
  
- **SuppressStartupBanner**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.  
  
   Daha fazla bilgi için bkz. [/nologo (başlangıç başlığını gösterme) (bağlayıcı)](https://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`, İşletim sistemine önce bağlayıcı çıkışını bir takas dosyasına kopyalamasını söyler ve sonra görüntüyü oradan çalıştırır.  
  
   Daha fazla bilgi için bkz `CD` . [/SWAPRUN (bağlayıcı çıktısını takas dosyasına yükle)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683)bağımsız değişkeni. Ayrıca bkz. **SwapRunFromNet** parametresi.  
  
- **SwapRunFromNET**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`, İşletim sistemine önce bağlayıcı çıkışını bir takas dosyasına kopyalamasını söyler ve sonra görüntüyü oradan çalıştırır.  
  
   Daha fazla bilgi için bkz `NET` . [/SWAPRUN (bağlayıcı çıktısını takas dosyasına yükle)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683)bağımsız değişkeni. Ayrıca bkz. bu tablodaki **SwapRunFromCD** parametresi.  
  
- **TargetMachine**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Program veya DLL için hedef platformu belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **NotSet** - *\<none>*  
  
  - **Machineard**  -  **/Machine: ARM**  
  
  - **Machineebc**  -  **/Machine: EBC**  
  
  - **MachineIA64**  -  **/MACHINE: IA64**  
  
  - **Machinemıps**  -  **/MACHINE: MIPS**  
  
  - **MachineMIPS16**  -  **/MACHINE: kayıtlardan biri mıps16**  
  
  - **Machinemıpsfpu**  -  **/MACHINE: MIPSFPU**  
  
  - **MachineMIPSFPU16**  -  **/MACHINE: MIPSFPU16**  
  
  - **MachineSH4**  -  **/MACHINE: sh4**  
  
  - **Machinethumb**  -  **/MACHINE: Thumb**  
  
  - **MachineX64**  -  **/Machine: x64**  
  
  - **MachineX86**  -  **/Machine: x86**  
  
    Daha fazla bilgi için bkz. [/Machine (hedef platformu belirt)](https://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`, Program görüntüsünün isteğe bağlı üst bilgisindeki IMAGE_OPTIONAL_HEADER Dllözellikler alanında bir bayrak ayarlar. Bu bayrak ayarlandığında, Terminal sunucusu uygulamada belirli değişiklikler yapmayacak.  
  
   Daha fazla bilgi için bkz. [/T saware (Terminal Server 'ı algılayan uygulama oluşturma)](https://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   İsteğe bağlı **dize** parametresi.  
  
   İzleyici günlüğünün dizinini belirtir.  
  
- **TreatLinkerWarningAsErrors**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , bağlayıcı bir uyarı oluşturursa çıkış dosyası üretilmez.  
  
   Daha fazla bilgi için bkz. [/WX (bağlayıcı uyarılarını hata olarak işle)](https://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   Varsa `true` , geçerli çıkış dosyası için .NET Framework derlemesi olmadan bir görüntü oluşturur.  
  
   Daha fazla bilgi için bkz. [/NOASSEMBLY (MSIL Modülü oluşturma)](https://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   . Tlb dosyasının dosya adı ve dosya adı uzantısını belirtir. Bir dosya adı veya yol ve dosya adı belirtin.  
  
   Daha fazla bilgi için bkz [./Tlhakkında (ad. TLB dosyası)](https://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   İsteğe bağlı **tamsayı** parametresi.  
  
   Bağlayıcı tarafından oluşturulan tür kitaplığı için Kullanıcı tarafından belirtilen bir değer belirtir. 1 ile 65535 arasında bir değer belirtin.  
  
   Daha fazla bilgi için bkz. [/Tldeklarasyon (TypeLib Için kaynak Kimliğini Belirt)](https://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **Uıacexecutionlevel**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Kullanıcı hesabı denetimiyle birlikte çalıştırıldığında, uygulama için istenen yürütme düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Daha fazla bilgi için bkz `level` . [/Bildiriestuac bağımsız değişkeni (bildirimdeki UAC bilgilerini katıştırır)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **Uıacuıaccess**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   `true`Uygulama, Kullanıcı arabirimi koruma düzeylerini ve sürücüler girişini masaüstündeki daha yüksek izin üzerine atlar; Aksi takdirde, `false` .  
  
   Daha fazla bilgi için bkz `uiAccess` . [/Bildiriestuac bağımsız değişkeni (bildirimdeki UAC bilgilerini katıştırır)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **Uselibrarydependencygirdileri**  
  
   İsteğe bağlı **Boolean** parametresi.  
  
   İse `true` , proje bağımlılıklarının kitaplık çıkışları ile bağlantılı olduğunda kitaplık dosyasının kendisi yerine kütüphaneian aracının girişleri kullanılır.  
  
- **Sürüm**  
  
   İsteğe bağlı **dize** parametresi.  
  
   . Exe veya. dll dosyasının üstbilgisine bir sürüm numarası koyun. " `major[.minor]` " Belirtin. `major`Ve `minor` bağımsız değişkenleri 0 ile 65535 arasında ondalık sayılardır.  
  
   Daha fazla bilgi için bkz. [/Version (sürüm bilgileri)](https://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
