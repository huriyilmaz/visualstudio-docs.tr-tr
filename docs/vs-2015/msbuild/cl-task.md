---
title: CL görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8307bc2c9efcbbab531754cd2d49fa18b04cc48a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698631"
---
# <a name="cl-task"></a>CL Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++ derleyici aracını sarmalanmış cl.exe. Derleyici yürütülebilir (. exe) dosyalar, dinamik bağlantı kitaplığı (. dll) dosyaları veya kod modülü (. netmodule) dosyaları oluşturur. Daha fazla bilgi için bkz. [derleyici seçenekleri](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, **CL** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.  
  
- **AdditionalIncludeDirectories**  
  
   İsteğe bağlı dize [] parametresi.  
  
   İçerme dosyaları için aranan dizinler listesine bir dizin ekler.  
  
   Daha fazla bilgi için bkz. [/i (ek Içerme dizinleri)](https://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   İsteğe bağlı dize parametresi.  
  
   Komut satırı seçeneklerinin listesi. Örneğin, "/*Seçenek1*  / *Seçenek2*  / *seçenek #*". Başka bir görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.  
  
   Daha fazla bilgi için bkz. [derleyici seçenekleri](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **Addiusingdizinleri** İsteğe bağlı dize [] parametresi.  
  
   **#Using** yönergesine geçirilen dosya başvurularını çözümlemek için derleyicinin arayacaktır bir dizin belirtir.  
  
   Daha fazla bilgi için bkz. [/AI (meta veri dizinlerini belirt)](https://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   İsteğe bağlı dize parametresi.  
  
   Her zaman komut satırına yayılan bir dize. Varsayılan değeri "**/c**" dir.  
  
- **Lerlistinglocation 'ı birleştirin**  
  
   Derleme kodu içeren bir listeleme dosyası oluşturur.  
  
   Daha fazla bilgi için/fa [,/FA (listeleme dosyası)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402)içindeki **/FA** seçeneğine bakın.  
  
- **Lerçıktıyı birleştirin**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleme kodu içeren bir listeleme dosyası oluşturur.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **NoList** - *\<none>*  
  
  - **Assemblycode**  -  **/FA**  
  
  - **Assemblyandmachinecode**  -  **/Fac**  
  
  - **Assemblyandsourcecode**  -  **/Fas**  
  
  - **Tümü**  -  **/FACS**  
  
    Daha fazla bilgi için/fa **,** **/fac**, **/Fas**ve/FA,/FA [(listeleme dosyası)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402)içindeki **/FACS** seçeneklerine bakın.  
  
- **Basicruntimedenetimleri**  
  
   İsteğe bağlı dize parametresi.  
  
   Çalışma zamanı hata denetimleri özelliğini, [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) pragma ile birlikte etkinleştirilir ve devre dışı bırakır.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılanını** -                          *\<none>*  
  
  - **StackFrameRuntimeCheck**  -  **/RTCs**  
  
  - **Unınitializedlocalusagecheck**  -  **/RTCu**  
  
  - **Enablefastdenetimleri**  -                           **/RTC1**  
  
    Daha fazla bilgi için bkz. [/RTC (çalışma zamanı hata denetimleri)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   İsteğe bağlı Boolean parametresi.  
  
   İse `true` , bir tarama bilgi dosyası oluşturur.  
  
   Daha fazla bilgi için/fr,/fr (Oluştur) içindeki **/fr** seçeneğine bakın [. Sbr dosyası)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   İsteğe bağlı dize parametresi.  
  
   Tarama bilgisi dosyası için bir dosya adı belirtir.  
  
   Daha fazla bilgi için bu tablodaki **BrowseInformation** parametresine bakın ve ayrıca bkz [./fr,/fr (oluştur. Sbr dosyası)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   İsteğe bağlı Boolean parametresi.  
  
   `true`, Dönüş adresinin üzerine yazılacak bazı arabellek taşmalarını algılar, bu da arabellek boyutu kısıtlamalarını zorlayamayan kodun yararlanmak için ortak bir tekniktir.  
  
   Daha fazla bilgi için bkz. [/GS (arabellek güvenlik denetimi)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
- **Buildingınıde**  
  
   İsteğe bağlı Boolean parametresi.  
  
   İse `true` , **MSBUILD** 'in IDE tarafından çağrıldığını gösterir. Aksi takdirde, **MSBuild** komut satırında çağrılır.  
  
- **CallingConvention**  
  
   İsteğe bağlı dize parametresi.  
  
   İşlev bağımsız değişkenlerinin yığına gönderilme sırasını belirleyen çağırma kuralını belirtir, çağıran işlevin veya çağrılan işlevin, çağrının sonundaki bağımsız değişkenleri yığından kaldırmasının yanı sıra derleyicinin bağımsız işlevleri tanımlamak için kullandığı ad dekorasyon kuralı.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Cdecl**  -  **/GD**  
  
  - **Fastcall**  -                           **/Gr**  
  
  - **Stdcall**  -                           **/Gz**  
  
    Daha fazla bilgi için bkz. [/GD,/gr,/GV,/GZ (çağırma kuralı)](https://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   İsteğe bağlı dize parametresi.  
  
   Giriş dosyasının C veya C++ kaynak dosyası olarak derlenmesi gerekip gerekmediğini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılanını** - *\<none>*  
  
  - **Compileasc**  -  **/TC**  
  
  - **Compileascpp**  -  **/TP**  
  
    Daha fazla bilgi için bkz. [/TC,/TP,/TC,/TP (kaynak dosya türünü belirtin)](https://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   İsteğe bağlı dize parametresi.  
  
   Uygulamaların ve bileşenlerin ortak dil çalışma zamanı (CLR) özelliklerini kullanmasına olanak sağlar.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **yanlýþ** - *\<none>*  
  
  - **doğru**  -  **/clr**  
  
  - **Saf**  -  **/clr: Pure**  
  
  - **Güvenli**  -  **/clr: Safe**  
  
  - **OldSyntax**  -  **/clr: oldSyntax**  
  
    Daha fazla bilgi için bkz. [/clr (ortak dil çalışma zamanı derlemesi)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **Createhotpatchableımage**  
  
   İsteğe bağlı Boolean parametresi.  
  
   İse `true` derleyiciye, *sık*yama için bir görüntü hazırlamasını söyler. Bu parametre, her işlevin ilk yönergesinin, sık yama için gerekli olan iki bayt olmasını sağlar.  
  
   Daha fazla bilgi için bkz. [/hotpatch (düzeltme eki eklenebilir görüntü oluşturma)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   İsteğe bağlı dize parametresi.  
  
   Programınız için oluşturulan hata ayıklama bilgileri türünü ve bu bilgilerin nesne (. obj) dosyalarında mi yoksa bir program veritabanı (PDB) içinde tutulup tutulmadığını seçer.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Eskistil**  -  **/Z7**  
  
  - **Programdatabase**  -  **/Zi**  
  
  - **Editandcontinue**  -  **/Zi**  
  
    Daha fazla bilgi için bkz. [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   İsteğe bağlı Boolean parametresi.  
  
   **True**ise, derleyiciye ANSI C veya ANSI C++ ile uyumlu olmayan dil yapıları için bir hata yaymasını söyler.  
  
   Daha fazla bilgi için [/za,/Ze (dil uzantılarını devre dışı bırak)](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)içindeki **/za** seçeneğine bakın.  
  
- **Disablespecificuyarılar**  
  
   İsteğe bağlı dize [] parametresi.  
  
   Noktalı virgülle ayrılmış bir listede belirtilen uyarı numaralarını devre dışı bırakır.  
  
   Daha fazla bilgi için `/wd` [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f)içindeki seçeneğe bakın.  
  
- **EnableEnhancedInstructionSet**  
  
   İsteğe bağlı dize parametresi.  
  
   Streaming SIMD Extensions (SSE) ve Streaming SIMD Extensions 2 (SSE2) yönergelerini kullanan kod oluşturma mimarisini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **StreamingSIMDExtensions**  -  **/Arch: SSE**  
  
  - **StreamingSIMDExtensions2**  -  **/Arch: SSE2**  
  
    Daha fazla bilgi için bkz. [/Arch (x86)](https://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **Enablefibersafeiyileştirmeleri**  
  
   İsteğe bağlı Boolean parametresi.  
  
   `true`, Statik iş parçacığı yerel depolama (kullanılarak ayrılan veriler) kullanılarak ayrılan veriler için fiber güvenliği destekler `__declspec(thread)` .  
  
   Daha fazla bilgi için bkz. [/gt (Fiber güvenli Iş parçacığı-yerel depolamayı destekle)](https://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   İsteğe bağlı Boolean parametresi.  
  
   İse `true` , Kod analizini etkinleştirin.  
  
   Daha fazla bilgi için bkz. [/analyze (kod analizi)](https://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   İsteğe bağlı dize parametresi.  
  
   İç derleyici hatası (ıCE) bilgilerini doğrudan Microsoft 'a sağlamanıza olanak tanır. Varsayılan olarak IDE derlemeleri ayarı **Prompt** olur ve komut satırı Derlemeleriyle ayarı **Queue**olur.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Hiçbiri**  -  **/errorreport: yok**  
  
  - **Komut istemi**  -  **/errorreport: Prompt**  
  
  - **Kuyruk**  -  **/errorreport: kuyruk**  
  
  - **Gönder**  -  **/errorreport: gönder**  
  
    Daha fazla bilgi için bkz. [/errorreport (Iç derleyici hatalarını raporla)](https://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   İsteğe bağlı dize parametresi.  
  
   Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **yanlýþ** - *\<none>*  
  
  - **Zaman uyumsuz**  -  **/EHa** dili  
  
  - **Eşitleme**  -  **/EHsc**  
  
  - **Synccthrow**  -  **/EHS**  
  
    Daha fazla bilgi için bkz. [/Eh (özel durum Işleme modeli)](https://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   İsteğe bağlı Boolean parametresi.  
  
   İse `true` , kaynak dosyaya eklenen genişletilmiş öznitelikleri olan bir listeleme dosyası oluşturur.  
  
   Daha fazla bilgi için bkz. [/FX (eklenen kodu Birleştir)](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   İsteğe bağlı dize parametresi.  
  
   Kod boyutunun veya kod hızının tercih edilip edilmeyeceğini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Tanımlanmadığından** - *\<none>*  
  
  - **Boyut**  -  **/OS**  
  
  - **Hız**  -  **/Ot**  
  
    Daha fazla bilgi için bkz. [/OS,/ot (küçük koda öncelik ver, hızlı kodu tercih et)](https://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   İsteğe bağlı Boolean parametresi.  
  
   `true`, Güvenilir kayan nokta özel durum modelini etkinleştirmesine izin vermez. Özel durumlar, tetiklendikten hemen sonra oluşturulur.  
  
   Daha fazla bilgi için bkz./fp içindeki/**FP: except** seçeneği [(kayan nokta davranışını belirt)](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   İsteğe bağlı dize parametresi.  
  
   Kayan nokta modelini ayarlar.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Kesin**  -  **/FP: kesin**  
  
  - **Katı**  -  **/FP: Strict**  
  
  - **Hızlı**  -  **/FP: Fast**  
  
    Daha fazla bilgi için bkz. [/FP (kayan nokta davranışını belirt)](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   İsteğe bağlı Boolean parametresi.  
  
   İse `true` , Microsoft uzantıları kullanan döngüler [için](https://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) ' de standart C++ davranışını uygular ([/ze](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Daha fazla bilgi için bkz. [/Zc: forScope (döngü kapsamında uygunluğu zorla)](https://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   İsteğe bağlı `String[]` parametre.  
  
   Önişlemci 'nin belirtilen bir veya daha fazla üst bilgi dosyasını işlemesini sağlar.  
  
   Daha fazla bilgi için bkz. [/Fi (zorunlu Içerme dosyasını Adlandır)](https://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Önişlemci 'nin belirtilen bir veya daha fazla **#using** dosyayı işlemesini sağlar.  
  
   Daha fazla bilgi için bkz. [/Fu (zorlanan #using dosyayı adlandır)](https://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **Functionlevellink**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, Derleyicinin paketlenmiş işlevler (Compts) biçiminde tek tek işlevleri paketleyip dağıtmalarını sağlar.  
  
   Daha fazla bilgi için bkz. [/GY (Işlev düzeyi bağlamayı etkinleştir)](https://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , derleyicinin kaynak kodu dosyalarındaki belge açıklamalarını işlemesini ve belge açıklamalarını içeren her kaynak kodu dosyası için bir. xdc dosyası oluşturmasını sağlar.  
  
   Daha fazla bilgi için bkz. [/doc (Işlem belgeleri açıklamaları) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Ayrıca bkz. bu tablodaki **Xmlbelgeadı** parametresi.  
  
- **Ignorestandardincludepath**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, DERLEYICININ yolda belirtilen dizinlerde ekleme ve ortam DEĞIŞKENLERINI içerme gibi dosyaları aramasını engeller.  
  
   Daha fazla bilgi için bkz. [/x (Standart Içerme yollarını yoksay)](https://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **Inlinefunctiongenişleme**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Derleme için satır içi işlev genişletmesinin düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılanını** - *\<none>*  
  
  - **Devre dışı**  -  **/Ob0**  
  
  - **Yalnızca açıkça satır içi**  -  **/OB1**  
  
  - **Anyuygun**  -  **/Ob2**  
  
    Daha fazla bilgi için bkz. [/ob (satır Içi Işlev genişletmesi)](https://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , uygulamanızın daha hızlı çalışmasına yardımcı olan işlevin iç veya diğer özel formlarıyla birlikte bazı işlev çağrılarını değiştirir.  
  
   Daha fazla bilgi için bkz. [/Oi (Iç Işlevler üret)](https://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **En az yeniden derleme**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, Değiştirilen c++ sınıf tanımlarını Içeren c++ kaynak dosyalarının (üst bilgi (. h) dosyalarına) yeniden derlenmesi gerekip gerekmediğini belirleyen, en az yeniden derlemeyi sunar.  
  
   Daha fazla bilgi için bkz. [/GD (en az yeniden derlemeyi etkinleştir)](https://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , derlemek için birden çok işlemci kullanın. Bu parametre, bilgisayarınızdaki her bir etkin işlemci için bir işlem oluşturur.  
  
   Daha fazla bilgi için bkz. [/MP (birden çok Işlemle derleme)](https://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Ayrıca bkz. bu tablodaki **ProcessorNumber** parametresi.  
  
- **ObjectFileName**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan yerine kullanılacak bir nesne (. obj) dosya adı veya dizin belirtir.  
  
   Daha fazla bilgi için bkz. [/fo (nesne dosyası adı)](https://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Nesne dosyalarının listesi.  
  
- **OmitDefaultLibName**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, Nesne (. obj) dosyasındaki varsayılan C çalışma zamanı kitaplık adını atlar. Varsayılan olarak, derleyici, bağlayıcıyı doğru kitaplığa yönlendirmek için kitaplığın adını. obj dosyasına koyar.  
  
   Daha fazla bilgi için bkz. [/zl (varsayılan kitaplık adını atla)](https://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **Omitframeişaretçiler**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.  
  
   Daha fazla bilgi için bkz. [/oy (çerçeve Işaretçisi atlama)](https://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , derleyicinin OpenMP yan tümceleri ve yönergeleri işlemesini sağlar.  
  
   Daha fazla bilgi için bkz. [/OpenMP (openmp 2,0 desteğini etkinleştir)](https://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **İyileştirme**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Hız ve boyut için çeşitli kod iyileştirmeleri belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Devre dışı**  -  **/Od**  
  
  - **Minspace**  -  **/O1**  
  
  - **Maxspeed**  -  **/O2**  
  
  - **Tam**  -  **/Ox**  
  
    Daha fazla bilgi için bkz. [/O Seçenekler (kodu iyileştirme)](https://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Derleme sırasında önceden derlenmiş üst bilgi (. pch) dosyası oluşturun veya kullanın.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **NotUsing** - *\<none>*  
  
  - **Oluştur**  -  **/Rivc**  
  
  - **Kullanım**  -  **/Yu**  
  
    Daha fazla bilgi için bkz. [/Yıc (ön derlenmiş üstbilgi dosyası oluştur)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) ve [/yu (önceden derlenmiş üst bilgi dosyası kullan)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Ayrıca, bu tablodaki **PrecompiledHeaderFile** ve **Precompiledheaderçıkışdosyası** parametrelerine bakın.  
  
- **PrecompiledHeaderFile**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Oluşturulacak veya kullanılacak ön derlenmiş üstbilgi dosyası adını belirtir.  
  
   Daha fazla bilgi için bkz. [/Yıc (ön derlenmiş üstbilgi dosyası oluştur)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) ve [/yu (önceden derlenmiş üst bilgi dosyası kullan)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **Precompiledheaderçıktıdosyası**  
  
   İsteğe bağlı **dize** parametresi.  
  
   Varsayılan yol adını kullanmak yerine önceden derlenmiş üst bilgi için bir yol adı belirtir.  
  
   Daha fazla bilgi için bkz [./fp (ad. PCH dosyası)](https://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , ön işleme sırasında açıklamaları korur.  
  
   Daha fazla bilgi için bkz. [/c (ön Işleme sırasında açıklamaları koru)](https://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   İsteğe bağlı `String[]` parametre.  
  
   Kaynak dosyanız için ön işleme sembolünü tanımlar.  
  
   Daha fazla bilgi için bkz. [/d (Önişlemci tanımları)](https://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   İsteğe bağlı `ITaskItem[]` parametre.  
  
   Görevler tarafından tüketilen ve yayılan bir Önişlemci çıkış öğeleri dizisi tanımlar.  
  
- **PreprocessOutputPath**  
  
   İsteğe bağlı `String` parametre.  
  
   **PreprocessToFile** parametresinin önceden işlenmiş çıktıyı yazdığı çıkış dosyasının adını belirtir.  
  
   Daha fazla bilgi için bkz. [/Fi (çıktı dosyası adını Önişle)](https://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , C ve C++ kaynak dosyalarını önceden işler ve önceden işlenen dosyaları standart çıkış cihazına kopyalar.  
  
   Daha fazla bilgi için bkz. [/EP (#line yönergeler olmadan stdout Için önceden işleme)](https://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   Eğer `true` , C ve C++ kaynak dosyalarını önişler ve önceden işlenmiş çıktıyı bir dosyaya yazar.  
  
   Daha fazla bilgi için bkz. [/p (bir dosyaya ön işlem)](https://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   İsteğe bağlı `Integer` parametre.  
  
   Çok işlemcili bir derlemede kullanılacak en fazla işlemci sayısını belirtir. **MultiProcessorCompilation** parametresiyle birlikte bu parametreyi kullanın.  
  
- **ProgramDataBaseFileName**  
  
   İsteğe bağlı `String` parametre.  
  
   Program veritabanı (PDB) dosyası için bir dosya adı belirtir.  
  
   Daha fazla bilgi için bkz. [/FD (program veritabanı dosya adı)](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   İsteğe bağlı `String` parametre.  
  
   Çok iş parçacıklı bir modülün bir DLL olup olmadığını belirtir ve çalışma zamanı kitaplığının perakende veya hata ayıklama sürümlerini seçer.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - Çok **Iş parçacıklı**  -  **/MT**  
  
  - **Multithreadeddebug**  -  **/MTD**  
  
  - **Multithreadeddll**  -  **/Md**  
  
  - **Multithreadeddebugdll**  -  **/MDD**  
  
    Daha fazla bilgi için bkz. [/MD,/MT,/LD (çalışma zamanı kitaplığını kullan)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , çalışma zamanında C++ nesne türlerini denetlemek için kod ekler (çalışma zamanı tür bilgisi).  
  
   Daha fazla bilgi için bkz. [/gr (çalışma zamanı türü bilgilerini etkinleştir)](https://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , derleyicinin içerme dosyalarının bir listesini çıktılarına neden olur.  
  
   Daha fazla bilgi için bkz. [/showIncludes (liste Içerme dosyaları)](https://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, Bir değer daha küçük bir veri türüne atanmışsa ve veri kaybına neden olursa bir çalışma zamanı hatası bildiriyor.  
  
   Daha fazla bilgi için [/RTC (çalışma zamanı hata denetimleri)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368)içindeki **/RTCC** seçeneğine bakın.  
  
- **Kaynaklar**  
  
   Gerekli `ITaskItem[]` parametre.  
  
   Boşluklarla ayrılmış kaynak dosyalarının bir listesini belirtir.  
  
- **StringPooling**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , derleyicinin program görüntüsünde özdeş dizelerin bir kopyasını oluşturmasını sağlar.  
  
   Daha fazla bilgi için bkz. [/GF (Yinelenen dizeleri ortadan kaldırma)](https://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
- **Structmemberhizalaması**  
  
   İsteğe bağlı `String` parametre.  
  
   Bir yapıdaki tüm üyelerin bayt hizalamasını belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - **Varsayılan**  -  **/ZP1**  
  
  - **1Bayt**  -  **/ZP1**  
  
  - **2 bayt**  -  **/ZP2**  
  
  - **4 bayt**  -  **/ZP4**  
  
  - **8 bayt**  -  **/ZP8**  
  
  - **16 bayt**  -  **/Zp16**  
  
    Daha fazla bilgi için bkz. [/Zp (struct üye hizalaması)](https://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.  
  
   Daha fazla bilgi için bkz. [/nologo (başlangıç başlığını gösterme) (C/C++)](https://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   İsteğe bağlı `String` parametre.  
  
   Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.  
  
   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.  
  
- **TreatSpecificWarningsAsErrors**  
  
   İsteğe bağlı **dize []** parametresi.  
  
   Belirtilen derleyici uyarıları listesini hata olarak değerlendirir.  
  
   Daha fazla bilgi için **/we** `n` [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f)içindeki/we seçeneğine bakın.  
  
- **TreatWarningAsError**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   Varsa `true` , tüm derleyici uyarılarını hata olarak değerlendirin.  
  
   Daha fazla bilgi için [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f)içindeki **/WX** seçeneğine bakın.  
  
- **TreatWChar_tAsBuiltInType**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, `wchar_t` Türü yerel bir tür olarak değerlendirin.  
  
   Daha fazla bilgi için bkz. [/Zc: wchar_t (wchar_t yerel tür)](https://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, Derleyicinin tanımladığı Microsoft 'a özgü sembolleri kaldırır.  
  
   Daha fazla bilgi için/u [,/u (simgeleri tanımla)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a)içindeki **/u** seçeneğine bakın.  
  
- **UndefinePreprocessorDefinitions**  
  
   İsteğe bağlı `String[]` parametre.  
  
   Tanımlanacak bir veya daha fazla önişlemci sembol listesini belirtir.  
  
   Daha fazla bilgi için/u [,/u,/u (sembolleri tanımlama)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a) **bölümüne bakın** .  
  
- **UseFullPaths**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , tanılamada derleyiciye geçirilen kaynak kodu dosyalarının tam yolunu görüntüler.  
  
   Daha fazla bilgi için bkz. [/FC (kaynak kodu dosyasının Tanılamadaki Tam yolu)](https://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **Useunicodefor, Lerlist**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , çıkış dosyasının UTF-8 biçiminde oluşturulmasına neden olur.  
  
   Daha fazla bilgi için [/FA,/FA (listeleme dosyası)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402)içindeki **/FAU** seçeneğine bakın.  
  
- **Uyarı düzeyi**  
  
   İsteğe bağlı `String` parametre.  
  
   Derleyici tarafından oluşturulacak en yüksek uyarı düzeyini belirtir.  
  
   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  
  
  - Birlikte **kapatma uyarıları**  -  **/W0**  
  
  - **Level1**  -  **/W1**  
  
  - **Level2**  -  **/W2**  
  
  - **Level3**  -  **/W3**  
  
  - **Level4**  -  **/W4**  
  
  - **Enablealluyarıları**  -  **/Duvar**  
  
    Daha fazla bilgi için [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/duvar,/WD,/we,/Wo,/WV,/WX (uyarı düzeyi)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f)içindeki **/w**_n_ seçeneğine bakın.  
  
- **WholeProgramOptimization**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , tüm program iyileştirmesini sunar.  
  
   Daha fazla bilgi için bkz. [/GL (tüm program iyileştirmesi)](https://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **Xmlbelgeadı**  
  
   İsteğe bağlı `String` parametre.  
  
   Oluşturulan XML belgesi dosyalarının adını belirtir. Bu parametre bir dosya veya dizin adı olabilir.  
  
   Daha fazla bilgi için bkz `name` . [/doc (Işlem belgeleri açıklamaları) içindeki bağımsız değişken (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Ayrıca bkz. bu tablodaki **GenerateXMLDocumentationFiles** parametresi.  
  
- **MinimalRebuildFromTracking**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   `true`, İzlenen bir artımlı derleme gerçekleştirilir; varsa `false` , yeniden oluşturma gerçekleştirilir.  
  
- **TLogReadFiles**  
  
   İsteğe bağlı `ITaskItem[]` parametre.  
  
   *Okuma dosyası izleme günlüklerini*temsil eden bir öğe dizisi belirtir.  
  
   Okuma dosyası izleme günlüğü (. TLog), bir görev tarafından okunan giriş dosyalarının adlarını içerir ve proje yapı sistemi tarafından artımlı derlemeleri desteklemek için kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.  
  
- **TLogWriteFiles**  
  
   İsteğe bağlı `ITaskItem[]` parametre.  
  
   *Yazma dosyası izleme günlüklerini*temsil eden bir öğe dizisi belirtir.  
  
   Yazma dosyası izleme günlüğü (. TLog), bir görev tarafından yazılan çıkış dosyalarının adlarını içerir ve proje yapı sistemi tarafından artımlı derlemeleri desteklemek için kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.  
  
- **TrackFileAccess**  
  
   İsteğe bağlı `Boolean` parametre.  
  
   İse `true` , dosya erişim desenlerini izler.  
  
   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
