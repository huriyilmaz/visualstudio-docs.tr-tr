---
title: 'İzlenecek yol: özel düzenleyiciye özellikler ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d14fb36298518409df34302f9346e186f0b0263
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825159"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>İzlenecek Yol: Bir Özel Düzenleyiciye Özellik Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel bir düzenleyici oluşturduktan sonra, ona daha fazla özellik ekleyebilirsiniz.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage için bir düzenleyici oluşturmak için  
  
1. Visual Studio Package proje şablonunu kullanarak özel bir düzenleyici oluşturun.  
  
     Daha fazla bilgi için bkz. [Izlenecek yol: özel bir düzenleyici oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2. Düzenleyicinizde tek bir görünümü veya birden çok görünümü destekleyip desteklemediğini belirleyin.  
  
     **Yeni pencere** komutunu destekleyen veya form görünümü ve kod görünümü olan bir düzenleyici, ayrı belge veri nesneleri ve belge görünümü nesneleri gerektirir. Yalnızca tek bir görünümü destekleyen bir düzenleyicide, belge verileri nesnesi ve belge görünümü nesnesi aynı nesne üzerinde uygulanabilir.  
  
     Birden çok görünüme örnek olarak bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).  
  
3. Arabirimini uygulayarak bir düzenleyici fabrikası uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
     Daha fazla bilgi için bkz. [Düzenleyici fabrikaları](../extensibility/editor-factories.md).  
  
4. Düzenleyici 'nin belge görünümü nesne penceresini yönetmek için yerinde etkinleştirme veya Basitleştirilmiş ekleme kullanmasını isteyip istemediğinize karar verin.  
  
     Basitleştirilmiş bir katıştırma Düzenleyicisi penceresi, standart bir belge görünümü barındırır, ancak yerinde etkinleştirme Düzenleyicisi penceresi, belge görünümü olarak bir ActiveX denetimi veya başka bir etkin nesne barındırır. Daha fazla bilgi için bkz. [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md) ve [yerinde etkinleştirme](../misc/in-place-activation.md).  
  
5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Komutları işlemek için arabirimini uygulayın.  
  
6. Aşağıdaki işlemleri gerçekleştirerek belge kalıcılığını ve dış dosya değişikliklerine yanıt verir:  
  
    1. Dosyayı kalıcı hale getirmek için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Düzenleyicinin belge verileri nesnesini uygulayın.  
  
    2. Dış dosya değişikliklerine yanıt vermek için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> Düzenleyicinin belge verisi nesnesine ve uygulayın.  
  
        > [!NOTE]
        > `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> İçin bir işaretçi almak üzere öğesini çağırın `IVsFileChangeEx` .  
  
7. Belgeyi koordine et kaynak kodu denetimiyle olayları düzenleyin. Bunu yapmak için:  
  
    1. Çağırarak öğesine bir işaretçi alın `IVsQueryEditQuerySave2` `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .  
  
    2. İlk düzenleme olayı gerçekleştiğinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemini çağırın.  
  
         Bu, kullanıcıdan zaten kullanıma alınmamış dosyayı denetlemesini ister. Hataları bulmak için bir "dosya kullanıma alınmamış" koşulunu işlediğinizden emin olun  
  
    3. Benzer şekilde, dosyayı kaydetmeden önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> yöntemini çağırın.  
  
         Bu yöntem, kullanıcının kaydedilmediyseniz veya son kaydetme işleminden sonra değiştirildiyse dosyayı kaydetmesini ister.  
  
8. Düzenleyicide Seçilen metnin özelliklerini göstermek için **Özellikler** penceresini etkinleştirin. Bunu yapmak için:  
  
    1. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>Metin seçimi her değiştiğinde, uygulamanızda geçiş yapılan her seferinde çağrı yapın <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
    2. `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> İçin bir işaretçi almak üzere hizmette çağrı yapın <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
9. Kullanıcıların, düzenleyici ve **araç kutusu**arasında veya dış düzenleyiciler (Microsoft Word gibi) ve **araç kutusu**arasında öğeleri sürükleyip bırakması için izin sağlayın. Bunu yapmak için:  
  
    1. `IDropTarget`Düzenleyicinize bir bırakma hedefi olduğunu IDE 'yi uyarmak için düzenleyicinize uygulayın.  
  
    2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>Düzenleyiciniz **araç kutusu**'ndaki öğeleri etkinleştirip devre dışı bırakabilmeniz için, bu arabirimi görünümde uygulayın.  
  
    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> Ve arayüzlerinin bir işaretçisini almak için hizmetini uygulayın ve çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> .  
  
         Bu, VSPackage 'ın **araç kutusuna**yeni öğeler eklemesini sağlar.  
  
10. Düzenleyiciniz için diğer isteğe bağlı özellikler isteyip istemediğinize karar verin.  
  
    - Düzenleyicinizde bul ve Değiştir komutlarını desteklemesini istiyorsanız, uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .  
  
    - Düzenleyicinizde bir belge anahattı araç penceresi kullanmak istiyorsanız, uygulayın `IVsDocOutlineProvider` .  
  
    - Düzenleyicinizde bir durum çubuğu kullanmak istiyorsanız, için <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> bir işaretçi almak üzere öğesini uygulayın ve çağırın `IVsStatusBar` .  
  
         Örneğin, bir düzenleyici, satır/sütun bilgilerini, seçim modunu (akış/kutu) ve ekleme modunu (INSERT/overstrı) görüntüleyebilir.  
  
    - Düzenleyicinizde komutunu desteklemesini istiyorsanız `Undo` , önerilen yöntem OLE Undo Manager modelini kullanmaktır. Alternatif olarak, düzenleyicinin `Undo` komutu doğrudan işlemesini sağlayabilirsiniz.  
  
11. VSPackage, menüler, düzenleyici ve diğer özellikler için GUID 'Ler dahil kayıt defteri bilgileri oluşturun.  
  
     Aşağıda, bir düzenleyiciyi doğru bir şekilde nasıl kaydedebileceğinizi göstermek için. RGS dosya betiğinizi yerleştireceğiniz genel bir kod örneği verilmiştir.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Bağlama duyarlı yardım desteği uygulayın.  
  
     Bu, düzenleyicinizdeki öğeler için F1 yardımı ve dinamik Yardım penceresi desteği sağlamanıza olanak tanır. Bunun hakkında daha fazla bilgi için bkz. [nasıl yapılır: düzenleyiciler Için bağlam sağlama](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Arabirimi uygulayarak düzenleyicinizden bir Otomasyon nesne modeli sunun `IDispatch` .  
  
     Daha fazla bilgi için bkz. [Otomasyon modeline katkıda bulunma](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Düzenleyici örneği, IDE yöntemi çağırdığında oluşturulur <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Düzenleyici birden çok görünümü destekliyorsa, `CreateEditorInstance` hem belge verileri hem de belge görünümü nesneleri oluşturur. Belge veri nesnesi zaten açıksa null olmayan bir `punkDocDataExisting` değer geçirilir `IVsEditorFactory::CreateEditorInstance` . Düzenleyici fabrikası uygulamanız, mevcut bir belge veri nesnesinin, üzerinde uygun arabirimler sorgulanarak uyumlu olup olmadığını belirlemelidir. Daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).  
  
- Basitleştirilmiş ekleme yaklaşımını kullanırsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirimini uygulayın.  
  
- Yerinde etkinleştirmeyi kullanmaya karar verirseniz, aşağıdaki arabirimleri uygulayın:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    > `IOleInPlaceComponent`Arabirim, OLE 2 menüsünü birleştirmeyi önlemek için kullanılır.  
  
     `IOleCommandTarget`Uygulamanız **Kes**, **Kopyala**ve **Yapıştır**gibi komutları işler. Uygulamasını uygularken `IOleCommandTarget` , Düzenleyicinizde kendi komut menü yapısını tanımlamak için kendi. vsct dosyasını gerektirip gerektirmediğini veya tarafından tanımlanan standart komutları uygulayamayacağını belirleyin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Genellikle düzenleyiciler IDE menülerini kullanır ve genişletir ve kendi araç çubuklarını tanımlar. Bununla birlikte, genellikle bir düzenleyici 'nin IDE 'nin standart komut kümesini kullanmanın yanı sıra kendi belirli komutlarını tanımlanması gerekir. Bunu yapmak için, Düzenleyicinizde kullandığı standart komutları bildirmelidir ve bir. vsct dosyasında yeni komutlar, bağlam menüleri, üst düzey menü ve araç çubukları tanımlayacaksınız. Yerinde etkinleştirme Düzenleyicisi oluşturursanız, <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> OLE 2 menü birleştirme kullanmak yerine bir. vsct dosyasında düzenleyici için menüleri ve araç çubuklarını uygulayın ve tanımlayın.  
  
- Kullanıcı arabiriminde menü komutunun kalabonu engellemek için, yeni komutları oluşturmadan önce IDE 'de var olan komutları kullanmanız gerekir. Paylaşılan komutlar SharedCmdDef. vsct ve ShellCmdDef. vsct içinde tanımlanır. Bu dosyalar, yüklemenizin VisualStudioIntegration\Common\Inc alt dizininde varsayılan olarak yüklenir [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- `ISelectionContainer` hem tek hem de birden çok seçimi ifade edebilir. Seçili her nesne bir nesne olarak uygulanır `IDispatch` .  
  
- IDE, ' `IOleUndoManager` dan <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> veya aracılığıyla örneklenebilir bir nesne olarak erişilebilen bir hizmet olarak uygular <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . Düzenleyiciniz `IOleUndoUnit` her bir eylem için arabirimini uygular `Undo` .  
  
- Özel bir düzenleyicinin Otomasyon nesnelerini kullanıma sunabilecekleri iki konum vardır:  
  
  - `Document.Object`  

  - `Window.Object`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomasyon modeline katkıda bulunma](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Nasıl Yapılır: Düzenleyiciler İçin Bağlam Sağlama](../extensibility/how-to-provide-context-for-editors.md)
