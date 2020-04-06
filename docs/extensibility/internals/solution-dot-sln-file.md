---
title: Çözüm (. Sln) dosyası
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705325"
---
# <a name="solution-sln-file"></a>Çözüm (.sln) dosyası

Çözüm Visual Studio'da proje düzenlemek için bir yapıdır. Çözüm, projeleriçin durum bilgilerini iki dosyada tutar:

- .sln dosyası (metin tabanlı, paylaşılan)

- .suo dosyası (ikili, kullanıcıya özel çözüm seçenekleri)

.suo dosyaları hakkında daha fazla bilgi için [Çözüm Kullanıcı Seçenekleri (. Suo) Dosya](../../extensibility/internals/solution-user-options-dot-suo-file.md).

VSPackage'ınız .sln dosyasında başvurulması sonucu yüklenirse, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> ortam .sln dosyasında okunmasını sağlar.

.sln dosyası, ortamın kalıcı veriler ve başvurulan proje VSPackages için ad değeri parametrelerini bulmak ve yüklemek için kullandığı metin tabanlı bilgileri içerir. Bir kullanıcı bir çözüm açtığında, çözüm, `preSolution` `Project`çözüm `postSolution` içindeki projeler ve çözüme bağlı kalıcı bilgiler yüklemek için .sln dosyasındaki ,, ve bilgiler arasında çevre döngüleri.

Her projenin dosyası, hiyerarşiyi o projenin öğeleriyle doldurmak için ortam tarafından okunan ek bilgiler içerir. Hiyerarşi veri kalıcılığı proje tarafından denetlenir. Veri normalde .sln dosyasında depolanmaz, ancak isterseniz proje bilgilerini kasıtlı olarak .sln dosyasına yazabilirsiniz. Kalıcılık hakkında daha fazla bilgi için [Project Kalıcılığı](../../extensibility/internals/project-persistence.md) ve [Proje Öğelerini Açma ve Kaydetme'ye](../../extensibility/internals/opening-and-saving-project-items.md)bakın.

## <a name="file-header"></a>Dosya üstbilgi

.sln dosyasının üstbilgisi aşağıdaki gibi görünür:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Tanımlar

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Dosya biçimi sürümünü tanımlayan standart üstbilgi.

`# Visual Studio 15`\
Visual Studio ana sürümü (en son) bu çözüm dosyası kaydedildi. Bu bilgiler, çözüm simgesindeki sürüm numarasını denetler.

`VisualStudioVersion = 15.0.26730.15`\
Visual Studio tam sürümü (en son) çözüm dosyası kaydedildi. Çözüm dosyası Visual Studio'nun aynı ana sürümüne sahip yeni bir sürümü tarafından kaydedilirse, bu değer çözüm dosyalarındaki karmaşayı azaltacak şekilde güncelleştirilemez.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Visual Studio'nun bu çözüm dosyasını açabilecek minimum (en eski) sürümü.

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
Dosya biçimi sürümünü tanımlayan standart üstbilgi.

`# Visual Studio Version 16`\
Visual Studio ana sürümü (en son) bu çözüm dosyası kaydedildi. Bu bilgiler, çözüm simgesindeki sürüm numarasını denetler.

`VisualStudioVersion = 16.0.28701.123`\
Visual Studio tam sürümü (en son) çözüm dosyası kaydedildi. Çözüm dosyası Visual Studio'nun aynı ana sürümüne sahip yeni bir sürümü tarafından kaydedilirse, bu değer dosyadaki karmaşayı azaltacak şekilde güncelleştirilemez.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Visual Studio'nun bu çözüm dosyasını açabilecek minimum (en eski) sürümü.

::: moniker-end

## <a name="file-body"></a>Dosya gövdesi

.sln dosyasının gövdesi, aşağıdaki gibi `GlobalSection`etiketlenmiş birkaç bölümden oluşur:

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

Bir çözüm yüklemek için ortam aşağıdaki görev sırasını gerçekleştirir:

1. Ortam .sln dosyasının Genel bölümünü okur ve `preSolution`işaretli tüm bölümleri işler. Bu örnek dosyada, böyle bir ifade vardır:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Ortam `GlobalSection('name')` etiketi okuduğunda, kayıt defterini kullanarak adı bir VSPackage ile eşler. Anahtar adı [HKLM\\<Uygulama Kimliği Kayıt Kökü\>\SolutionPersistence\AggregateGUIDs] altında kayıt defterinde bulunmalıdır. Anahtarların varsayılan değeri, girişleri yazan VSPackage'ın Paket GUID'idir (REG_SZ).

2. Ortam VSPackage yükler, `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> arayüz için VSPackage çağırır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> VSPackage verileri depolayabilir, böylece bölümünde veri ile yöntemi çağırır. Ortam her `preSolution` bölüm için bu işlemi yineler.

3. Ortam, proje kalıcılığı blokları aracılığıyla yineler. Bu durumda, bir proje vardır.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Bu deyim, benzersiz proje GUID ve proje türü GUID içerir. Bu bilgiler, proje dosyasını veya çözüme ait dosyaları ve her proje için gereken VSPackage'ı bulmak için ortam tarafından kullanılır. Proje GUID proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> ile ilgili belirli VSPackage yüklemek için geçirilir, daha sonra proje VSPackage tarafından yüklenir. Bu durumda, bu proje için yüklenen VSPackage Visual Basic'tir.

   Her proje, çözümdeki diğer projeler tarafından gerektiği gibi erişilebilmek için benzersiz bir proje örnek kimliği kalıcı olabilir. İdeal olarak, çözüm ve projeler kaynak kodu denetimi altındaysa, projeye giden yol çözüme giden yol ile göreli olmalıdır. Çözüm ilk yüklendiğinde, proje dosyaları kullanıcının makinesinde olamaz. Proje dosyasının çözüm dosyasına göre sunucuda depolanmasıyla, proje dosyasının bulunması ve kullanıcının makinesine kopyalanması nispeten kolaydır. Daha sonra, proje için gereken diğer dosyaları kopyalar ve yükler.

4. .sln dosyasının proje bölümünde yer alan bilgilere göre, ortam her proje dosyasını yükler. Projenin kendisi daha sonra proje hiyerarşisini doldurmak ve iç içe olan projeleri yüklemekten sorumludur.

5. .sln dosyasının tüm bölümleri işlendikten sonra çözüm Çözüm Gezgini'nde görüntülenir ve kullanıcı tarafından değiştirilen kullanıma hazırdır.

Çözümde proje yi uygulayan herhangi bir VSPackage yüklenmezse, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> yöntem çağrılır ve çözümdeki diğer tüm projelere yükleme sırasında yapmış olabileceği değişiklikleri yoksayma şansı verilir. Ayrıştırma hataları oluşursa, çözüm dosyalarıyla mümkün olduğunca çok bilgi korunur ve ortam, kullanıcıyı çözümün bozuk olduğu konusunda uyaran bir iletişim kutusu görüntüler.

Çözüm kaydedildiğinde veya kapatıldığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> .sln dosyasına girilmesi gereken çözümde değişiklik yapIlip yapılmadığını görmek için yöntem çağrılır ve hiyerarşiye geçirilir. `QuerySaveSolutionProps` "Içinde" <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>olarak geçirilen null değeri, çözüm için bilgilerin kalıcı olduğunu gösterir. Değer null değilse, kalıcı bilgiler <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimin işaretçitarafından belirlenen belirli bir proje içindir.

Kaydedilecek bilgi varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> yönteme işaretçiile çağrılır. Yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> daha sonra arabirimden `IPropertyBag` ad değeri çiftleri almak ve .sln dosyasına bilgi yazmak için ortam tarafından çağrılır.

`SaveSolutionProps`ve `WriteSolutionProps` nesneler, tüm değişiklikler .sln dosyasına girilene kadar `IPropertyBag` arabirimden kaydedilecek bilgileri almak için ortam tarafından özyinelemeli olarak çağrılır. Bu şekilde, bilgilerin çözümle devam edeceğinden ve çözüm bir sonraki açıldığında kullanılabilir olmasını sağlayabilirsiniz.

Yüklenen her VSPackage.sln dosyasına kaydedilen bir şey olup olmadığını görmek için numaralandırılır. Kayıt defteri anahtarları yalnızca yükleme zamanında sorgulanır. Ortam, yüklenen paketlerin tümünün çözümü kaydedildiği anda bellekte olduğundan bilir.

Yalnızca .sln dosyası `preSolution` ve `postSolution` bölümlerdeki girişleri içerir. Çözümün düzgün yüklenmesi için bu bilgilere ihtiyaç duyduğundan.suo dosyasında benzer bölümler yoktur. .suo dosyası, kaynak kodu denetimi altında paylaşılmak veya yerleştirilmeye yönelik olmayan özel notlar gibi kullanıcıya özgü seçenekler içerir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Çözüm Kullanıcı Seçenekleri (. Suo) Dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Çözümler](../../extensibility/internals/solutions-overview.md)
