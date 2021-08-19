---
title: Çözüm (. Sln) dosyası
description: Bir projenin durum bilgilerini Visual Studio.sln dosyası hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5c036504bd5a7b881edab2d2bf4ef373706d65f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062751"
---
# <a name="solution-sln-file"></a>Çözüm (.sln) dosyası

Çözüm, proje düzenlemeye yönelik bir yapıdır ve Visual Studio. Çözüm, projelerin durum bilgilerini iki dosyada sürdürür:

- .sln dosyası (metin tabanlı, paylaşılan)

- .suo dosyası (ikili, kullanıcıya özgü çözüm seçenekleri)

.suo dosyaları hakkında daha fazla bilgi için bkz. [Çözüm Kullanıcı Seçenekleri (. Suo) Dosyası.](../../extensibility/internals/solution-user-options-dot-suo-file.md)

VSPackage dosyanız .sln dosyasında başvuruldu sonucu olarak yüklenirse, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln dosyasında okumak için çağrır.

.sln dosyası, ortamın kalıcı veriler için ad-değer parametrelerini bulup yüklemek için kullandığı metin tabanlı bilgileri içerir ve proje VSPackages'a başvurur. Kullanıcı bir çözüm açtığında, ortam çözümü, çözüm içindeki projeleri ve çözüme eklenmiş kalıcı bilgileri yüklemek için .sln dosyasındaki , ve bilgilerinde `preSolution` `Project` `postSolution` döngüler açar.

Her projenin dosyası, hiyerarşiyi bu projenin öğeleriyle doldurmak için ortam tarafından okunan ek bilgiler içerir. Hiyerarşi veri kalıcılığı proje tarafından denetlenr. Normalde veriler .sln dosyasında depolanmaz, ancak bunu tercih ediyorsanız proje bilgilerini kasıtlı olarak .sln dosyasına yazabilirsiniz. Kalıcılık hakkında daha fazla bilgi için [bkz. Project Kalıcılık](../../extensibility/internals/project-persistence.md) ve Öğeleri [Açma Project Kaydetme.](../../extensibility/internals/opening-and-saving-project-items.md)

## <a name="file-header"></a>Dosya üst bilgisi

.sln dosyasının üst bilgisi şu şekilde görünür:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Tanımlar

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Dosya biçimi sürümünü tanımlayan standart üst bilgi.

`# Visual Studio 15`\
Bu çözümün ana Visual Studio (en son) bu çözüm dosyasını kaydeden sürümüdür. Bu bilgiler çözüm simgesinde sürüm numarasını kontrol eder.

`VisualStudioVersion = 15.0.26730.15`\
Çözüm dosyasının Visual Studio (en son) tam sürümü. Çözüm dosyası aynı ana sürüme sahip olan Visual Studio sürümü tarafından kaydedilirse, çözüm dosyalarında churn'u daha az olacak şekilde bu değer güncelleştirilmez.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Bu çözüm dosyasını aç Visual Studio en düşük (en eski) sürüm.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Tanımlar

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Dosya biçimi sürümünü tanımlayan standart üst bilgi.

`# Visual Studio Version 16`\
Bu çözümün ana Visual Studio (en son) bu çözüm dosyasını kaydeden sürümüdür. Bu bilgiler çözüm simgesinde sürüm numarasını kontrol eder.

`VisualStudioVersion = 16.0.28701.123`\
Çözüm dosyasının Visual Studio (en son) tam sürümü. Çözüm dosyası aynı ana sürüme sahip Visual Studio yeni bir sürüm tarafından kaydedilirse, dosyada daha az verim olacak şekilde bu değer güncelleştirilmez.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Bu çözüm dosyasını aç Visual Studio en düşük (en eski) sürüm.

::: moniker-end

## <a name="file-body"></a>Dosya gövdesi

.sln dosyasının gövdesi, aşağıdaki gibi etiketlenmiş birkaç `GlobalSection` bölümden oluşur:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Bir çözümü yüklemek için ortam aşağıdaki görev dizisini gerçekleştirir:

1. Ortam, .sln dosyasının Genel bölümünü okur ve işaretlenmiş tüm bölümleri `preSolution` işler. Bu örnek dosyada böyle bir deyim vardır:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Ortam etiketi `GlobalSection('name')` okuduğunda, kayıt defterini kullanarak adı vsPackage ile eşler. Anahtar adı kayıt defterinde [HKLM<Uygulama Kimliği \\ Kayıt Defteri Kökü \> \SolutionPersistence\AggregateGUIDs] altında mevcut olması gerekir. Anahtarların varsayılan değeri, vsPackage'ın REG_SZ paket GUID'si (REG_SZ) değeridir.

2. Ortam VSPackage'i yükler, arabirim için VSPackage'a çağrılar ve VSPackage'ın verileri depolay için bölümündeki `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> verilerle yöntemini çağırır. Ortam bu işlemi her bölüm için `preSolution` tekrarlar.

3. Ortam, proje kalıcılığı bloklarında da aynı şekilde devam eder. Bu durumda bir proje var.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Bu deyim benzersiz proje GUID'sini ve proje türü GUID'sini içerir. Bu bilgiler ortam tarafından çözüme ait proje dosyasını veya dosyalarını ve her proje için gereken VSPackage'ı bulmak için kullanılır. ProjeYLE ilgili belirli VSPackage'ı yüklemek için proje GUID'si'ne geçirildi, ardından proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> VSPackage tarafından yüklenir. Bu durumda, bu proje için yüklenen VSPackage Visual Basic.

   Her proje, çözümde diğer projeler tarafından gerektiğinde erişilebilecek benzersiz bir proje örneği kimliği kalıcı olabilir. İdeal olarak, çözüm ve projeler kaynak kodu denetimi altında ise, projenin yolu çözümün yoluyla göreli olması gerekir. Çözüm ilk yüklendiğinde proje dosyaları kullanıcının makinesine yüklenemiyor. Proje dosyasının çözüm dosyasıyla göreli olarak sunucuda depolanmış olması, proje dosyasının bulunarak kullanıcının makinesine kopyalandığı için oldukça basittir. Ardından proje için gereken diğer dosyaları kopyalar ve yükler.

4. Ortam, .sln dosyasının proje bölümünde yer alan bilgilere bağlı olarak her proje dosyasını yükler. Projenin kendisi daha sonra proje hiyerarşisini doldurmak ve iç içe geçmiş projeleri yüklemeden sorumludur.

5. .sln dosyasının tüm bölümleri işlendikten sonra, çözüm Çözüm Gezgini olarak görüntülenir ve kullanıcı tarafından değişiklik yapmaya hazırdır.

Çözümde bir proje uygulayan herhangi bir VSPackage yüklenemezse yöntem çağrılır ve çözümde yer alan diğer tüm projelerde yükleme sırasında yapmış olabileceği değişiklikleri yoksayma şansı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> verilir. Ayrıştırma hataları oluşursa, çözüm dosyalarıyla mümkün olduğunca çok bilgi korunur ve ortam, kullanıcıya çözümün bozuk olduğunu gösteren bir iletişim kutusu görüntüler.

Çözüm kaydedilse veya kapatıldıklarında yöntemi çağrılır ve .sln dosyasına giril ihtiyacı olan çözümde değişiklik yapıp yapıldığını görmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> hiyerarşiye geçirilir. içinde 'ye geçirilen null `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> değer, çözüm için bilgilerin kalıcı olduğunu gösterir. Değer null ise kalıcı bilgiler, arabirim işaretçisi tarafından belirlenen belirli bir projeye <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> yöneliktir.

Kaydedilen bilgiler varsa, arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> yöntemine bir işaretçi ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> çağrılır. Yöntem daha sonra arabirimden ad-değer çiftlerini almak ve bilgileri .sln dosyasına yazmak için ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> `IPropertyBag` tarafından çağrılır.

`SaveSolutionProps` ve nesneleri, tüm değişiklikler .sln dosyasına girilene kadar arabirimden kaydedilinceye kadar bilgileri almak için ortam tarafından tekrar tekrar `WriteSolutionProps` `IPropertyBag` çağrılır. Bu şekilde, bilgilerin çözümde kalıcı ve çözüm bir sonraki açılabilir durumda olacağını doğrular.

Yüklenen her VSPackage, .sln dosyasına kaydedilemediklerini görmek için numaralandı. Yalnızca yükleme zamanında kayıt defteri anahtarları sorgulandı. Ortam, çözümün kaydedi olduğu sırada bellekte olduğundan yüklenen paketlerin hepsini bilir.

Yalnızca .sln dosyası ve bölümlerinde `preSolution` girdileri `postSolution` içerir. Çözüm, bu bilgilerin düzgün bir şekilde yüklenmeye ihtiyacı olduğu için .suo dosyasında benzer bölümler yoktur. .suo dosyası, özel notlar gibi kullanıcıya özgü, kaynak kodu denetimi altında paylaşılmaya veya altına yerleştirilma amacına sahip olmayan seçenekler içerir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Çözüm Kullanıcı Seçenekleri (.Suo) Dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Çözümler](../../extensibility/internals/solutions-overview.md)
