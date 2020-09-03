---
title: Çözüm (. Sln) dosyası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154968"
---
# <a name="solution-sln-file"></a>Çözüm (.Sln) Dosyası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çözüm, Visual Studio 'da proje düzenlemek için bir yapıdır. Çözüm,. sln (metin tabanlı, paylaşılan) ve. suo (ikili, kullanıcıya özel çözüm seçenekleri) dosyalarındaki projelere ait durum bilgilerini tutar. . Suo dosyaları hakkında daha fazla bilgi için bkz. [çözüm Kullanıcı seçenekleri (. Suo) dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 VSPackage,. sln dosyasında başvurulmakta olan bir sonuç olarak yüklenirse, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> . sln dosyasında okumak için çağırır.  
  
 . Sln dosyası, kalıcı veriler ve başvurduğu VSPackages projesi için ad-değer parametrelerini bulmak ve yüklemek üzere ortam tarafından kullanılan metin tabanlı bilgiler içerir. Bir Kullanıcı bir çözüm açtığında, ortam, `preSolution` `Project` ve çözümü `postSolution` yüklemek için. sln dosyasındaki bilgileri, çözüm içindeki projeleri ve çözüme ekli kalıcı bilgileri geçer.  
  
 Her projenin dosyası, hiyerarşiyi ilgili projenin öğeleriyle doldurmak için ortam tarafından okunan ek bilgiler içerir. Hiyerarşi verilerinin kalıcılığı proje tarafından denetlenir; veriler normalde. sln dosyasında depolanmaz, ancak bunu yapmak istiyorsanız, kasıtlı olarak proje bilgilerini. sln dosyasına yazabilirsiniz. Kalıcılık hakkında daha fazla bilgi için bkz. [Proje kalıcılığı](../../extensibility/internals/project-persistence.md) ve [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Çözüm dosyası Içeriği  
 . Sln dosyası, aşağıdaki kodda gösterildiği gibi birkaç bölümden oluşur.  
  
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
  
 Bir çözümü yüklemek için, ortam aşağıdaki görev sırasını gerçekleştirir.  
  
1. Ortam,. sln dosyasının genel bölümünü okur ve işaretlenen tüm bölümleri işler `preSolution` . Bu durumda, böyle bir ifade vardır:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Ortam etiketi okuduğunda `GlobalSection('name')` , kayıt defterini kullanarak adı VSPackage ile eşler. Anahtar adı [HKLM \\<uygulama kimliği kayıt defteri kökü \> \ Solutionpersistence\aggregateıds] altındaki kayıt defterinde bulunmalıdır. Anahtarların varsayılan değeri, girdileri yazan VSPackage 'ın paket GUID 'sidir (REG_SZ).  
  
2. Ortam, VSPackage 'ı yükler, `QueryInterface` arabirim Için VSPackage üzerinde çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> ve yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> VSPackage 'un verileri depolayabilmesi için bölümündeki verilerle çağırır. Ortam, her bölüm için bu işlemi yineler `preSolution` .  
  
3. Ortam, proje Kalıcılık blokları boyunca yinelenir. Bu durumda, bir proje vardır.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Bu ifade, benzersiz proje GUID 'ini ve proje türü GUID 'sini içerir. Bu bilgiler, bir proje dosyası ya da çözüme ait olan dosyaları ve her proje için gereken VSPackage 'ı bulmak için ortam tarafından kullanılır. Proje GUID 'SI, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> projeyle ilgili belirli VSPackage 'ı yüklemek için öğesine geçirilir, ardından Proje VSPackage tarafından yüklenir. Bu durumda, bu proje için yüklenen VSPackage Visual Basic.  
  
    Her proje, çözümdeki diğer projelerin gerektiği şekilde erişilebilmesi için benzersiz bir proje örneği KIMLIĞINI kalıcı hale getirebilirler. İdeal olarak, çözüm ve projeler kaynak kodu denetimi altındaysa, projenin yolu çözümün yoluna göre olmalıdır. Çözüm ilk yüklendiğinde, proje dosyaları kullanıcının makinesinde olamaz. Proje dosyasının, çözüm dosyası ile ilişkili sunucuda depolanmasından sonra, proje dosyasının bulunması ve kullanıcının makinesine kopyalanması oldukça basittir. Daha sonra, proje için gereken dosyaları kopyalar ve geri yükler.  
  
4. . Sln dosyasının proje bölümünde yer alan bilgilere bağlı olarak, ortam her bir proje dosyasını yükler. Projenin kendisi bundan sonra proje hiyerarşisinin doldurulmasından ve iç içe geçmiş projelerin yüklenmesine sorumludur.  
  
5. . Sln dosyasının tüm bölümleri işlendikten sonra, çözüm Çözüm Gezgini görüntülenir ve Kullanıcı tarafından değiştirilmek üzere hazırdır.  
  
   Çözümdeki bir projeyi uygulayan herhangi bir VSPackage yükleme başarısız olursa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> yöntemi çağrılır ve çözümdeki diğer tüm projeler, yükleme sırasında yapmış olabileceği değişiklikleri yok saymaya bir şans vermiş olur. Ayrıştırma hataları oluşursa, çözüm dosyalarıyla mümkün olduğunca fazla bilgi korunur ve ortam, kullanıcının çözümün bozuk olduğunu bildiren bir iletişim kutusu görüntüler.  
  
   Çözüm kaydedildiğinde veya kapatıldığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Yöntem,. sln dosyasına girilmesi gereken çözümde değişiklik yapıldığını görmek için çağrılır ve hiyerarşiye geçirilir. İçinde öğesine geçirilen null değeri `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , çözüm için bilgilerin kalıcı olduğunu gösterir. Değer null değilse, kalıcı bilgiler arabirimin işaretçisi tarafından belirlenen belirli bir proje içindir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .  
  
   Kaydedilecek bilgiler varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> arabirimi yöntemine yönelik bir işaretçi ile çağırılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>Daha sonra yöntemi, arabirimden ad-değer çiftlerini almak `IPropertyBag` ve bilgileri. sln dosyasına yazmak için ortamı tarafından çağrılır.  
  
   `SaveSolutionProps` ve `WriteSolutionProps` nesneler, `IPropertyBag` . sln dosyasına tüm değişiklikler girilene kadar arabirimden kaydedilecek bilgileri almak için ortam tarafından yinelemeli olarak çağrılır. Bu şekilde, bilgilerin çözümle kalıcı olacağını ve çözümün bir sonraki açılışında kullanılabilmesini sağlayabilirsiniz.  
  
   Yüklenen her VSPackage,. sln dosyasına kaydedilecek bir şey olup olmadığını görmek için numaralandırılır. Yalnızca kayıt defteri anahtarlarının sorgulandığı yükleme sırasında olur. Ortam, çözüm kaydedildiği sırada bellekte olduklarından yüklenen paketlerin tümünü bilir.  
  
   Yalnızca. sln dosyası, ve bölümlerindeki girdileri içerir `preSolution` `postSolution` . Çözümün bu bilgilerin düzgün şekilde yüklenmesi gerektiğinden,. suo dosyasında benzer bir bölüm yoktur. . Suo dosyası, kaynak kodu denetimi altına paylaşılması veya yerleştirilmesi amaçlanan özel notlar gibi kullanıcıya özgü seçenekleri içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Çözüm Kullanıcı seçenekleri (. Suo) dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Çözümler](../../extensibility/internals/solutions-overview.md)
