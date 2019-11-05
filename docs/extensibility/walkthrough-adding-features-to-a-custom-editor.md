---
title: 'İzlenecek yol: özel düzenleyiciye özellikler ekleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fa926b21171c3e09b5a0f4d74e9415da090bf2f
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73569072"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>İzlenecek yol: özel düzenleyiciye özellikler ekleme
Özel bir düzenleyici oluşturduktan sonra, ona daha fazla özellik ekleyebilirsiniz.

## <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage için bir düzenleyici oluşturmak için

1. Visual Studio Package proje şablonunu kullanarak özel bir düzenleyici oluşturun.

     Daha fazla bilgi için bkz. [Izlenecek yol: özel düzenleyici oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Düzenleyicinizde tek bir görünümü veya birden çok görünümü destekleyip desteklemediğini belirleyin.

     **Yeni pencere** komutunu destekleyen veya form görünümü ve kod görünümü olan bir düzenleyici, ayrı belge veri nesneleri ve belge görünümü nesneleri gerektirir. Yalnızca tek bir görünümü destekleyen bir düzenleyicide, belge verileri nesnesi ve belge görünümü nesnesi aynı nesne üzerinde uygulanabilir.

     Birden çok görünüme örnek olarak bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> arabirimini ayarlayarak bir düzenleyici fabrikası uygulayın.

     Daha fazla bilgi için bkz. [Düzenleyici fabrikaları](../extensibility/editor-factories.md).

4. Düzenleyici 'nin belge görünümü nesne penceresini yönetmek için yerinde etkinleştirme veya Basitleştirilmiş ekleme kullanmasını isteyip istemediğinize karar verin.

     Basitleştirilmiş bir katıştırma Düzenleyicisi penceresi, standart bir belge görünümü barındırır, ancak yerinde etkinleştirme Düzenleyicisi penceresi, belge görünümü olarak bir ActiveX denetimi veya başka bir etkin nesne barındırır. Daha fazla bilgi için bkz. [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md) ve [yerinde etkinleştirme](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Komutları işlemek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimini uygulayın.

6. Belge kalıcılığını ve dış dosya değişikliklerine yanıt sağlama:

    1. Dosyayı kalıcı hale getirmek için, düzenleyicinin belge verileri nesnesinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> uygulayın.

    2. Dış dosya değişikliklerine yanıt vermek için, düzenleyicinin belge verileri nesnesinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> uygulayın.

        > [!NOTE]
        > `IVsFileChangeEx`işaretçiyi almak için <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> `QueryService` çağırın.

7. Belgeyi koordine et kaynak kodu denetimiyle olayları düzenleyin. Aşağıdaki adımları uygulayın:

    1. <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>`QueryService` çağırarak `IVsQueryEditQuerySave2` bir işaretçi alın.

    2. İlk düzenleme olayı gerçekleştiğinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemini çağırın.

         Bu yöntem, kullanıcının zaten kullanıma almadığından dosyayı kullanıma almak isteyip istemediğinizi sorar. Hataları bulmak için bir "dosya kullanıma alınmamış" koşulunu işlediğinizden emin olun.

    3. Benzer şekilde, dosyayı kaydetmeden önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> yöntemini çağırın.

         Bu yöntem, kullanıcının kaydedilmediyse veya son kaydetme işleminden sonra değiştirildiyse dosyayı kaydetmesini ister.

8. Düzenleyicide Seçilen metnin özelliklerini göstermek için **Özellikler** penceresini etkinleştirin. Aşağıdaki adımları uygulayın:

    1. Metin seçimi her değiştiğinde <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> çağırın ve <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>uygulamanızda geçiş yapın.

    2. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>işaretçiyi almak için <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> hizmetinde `QueryService` çağırın.

9. Kullanıcıların, düzenleyici ve **araç kutusu**arasında veya dış düzenleyiciler (Microsoft Word gibi) ve **araç kutusu**arasında öğeleri sürükleyip bırakması için izin sağlayın. Aşağıdaki adımları uygulayın:

    1. Düzenleyicinizde düzenleyicinin bir bırakma hedefi olduğu IDE 'yi uyarmak için `IDropTarget` uygulayın.

    2. Düzenleyicinizde **araç kutusundaki**öğeleri etkinleştirip devre dışı bırakabilmeniz için <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> arabirimini görünümünde uygulayın.

    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> arabirimlerine bir işaretçi almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> uygulayın ve <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> hizmetinde `QueryService` çağırın.

         Bu adımlar, VSPackage 'ın **araç kutusuna**yeni öğeler eklemesini sağlar.

10. Düzenleyiciniz için diğer isteğe bağlı özellikler isteyip istemediğinize karar verin.

    - Düzenleyicinizde bul ve Değiştir komutlarını desteklemesini istiyorsanız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>uygulayın.

    - Düzenleyicinizde bir belge anahattı araç penceresi kullanmak istiyorsanız, `IVsDocOutlineProvider`uygulayın.

    - Düzenleyicinizde bir durum çubuğu kullanmak istiyorsanız, `IVsStatusBar`bir işaretçi almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> uygulayın ve <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> için `QueryService` çağırın.

         Örneğin, bir düzenleyici, satır/sütun bilgilerini, seçim modunu (akış/kutu) ve ekleme modunu (INSERT/overstrı) görüntüleyebilir.

    - Düzenleyicinin `Undo` komutunu desteklemesini istiyorsanız, önerilen yöntem OLE Undo Manager modelini kullanmaktır. Alternatif olarak, düzenleyicinin `Undo` komutu doğrudan işlemesini sağlayabilirsiniz.

11. VSPackage, menüler, düzenleyici ve diğer özellikler için GUID 'Ler dahil kayıt defteri bilgileri oluşturun.

     Aşağıda, bir düzenleyiciyi doğru bir şekilde nasıl kaydedebileceğinizi göstermek için *. rgs* dosya betiğinizi yerleştireceğiniz genel bir kod örneği verilmiştir.

    ```csharp
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

     Bu adım, düzenleyicinizdeki öğeler için F1 yardımı ve dinamik Yardım penceresi desteği sağlamanıza olanak tanır. Daha fazla bilgi için bkz. [nasıl yapılır: düzenleyiciler için bağlam sağlama](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. `IDispatch` arabirimini uygulayarak düzenleyicinizden bir Otomasyon nesne modeli sunun.

     Daha fazla bilgi için bkz. [Otomasyon modeline katkıda bulunma](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Güçlü programlama

- Düzenleyici örneği, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemini çağırdığında oluşturulur. Düzenleyici birden çok görünümü destekliyorsa, `CreateEditorInstance` hem belge verileri hem de belge görünümü nesneleri oluşturur. Belge verileri nesnesi zaten açıksa, `IVsEditorFactory::CreateEditorInstance`null olmayan bir `punkDocDataExisting` değeri geçirilir. Düzenleyici fabrikası uygulamanız, mevcut bir belge veri nesnesinin, üzerinde uygun arabirimler sorgulanarak uyumlu olup olmadığını belirlemelidir. Daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).

- Basitleştirilmiş ekleme yaklaşımını kullanırsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirimini uygulayın.

- Yerinde etkinleştirmeyi kullanmaya karar verirseniz, aşağıdaki arabirimleri uygulayın:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > `IOleInPlaceComponent` arabirimi OLE 2 menüsünü birleştirmenin önüne geçmek için kullanılır.

   `IOleCommandTarget` uygulamanız **Kes**, **Kopyala**ve **Yapıştır**gibi komutları işler. `IOleCommandTarget`uygularken, düzenleyicinin kendi komut menü yapısını tanımlamak için kendi *. vsct* dosyasını gerektirip gerektirmediğini veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tarafından tanımlanan standart komutları uygulayamayacağını belirleyin. Genellikle düzenleyiciler IDE menülerini kullanır ve genişletir ve kendi araç çubuklarını tanımlar. Bununla birlikte, genellikle bir düzenleyicinin IDE 'nin standart komut kümesini kullanmaya ek olarak kendi belirli komutlarını tanımlanması gerekir. Düzenleyiciniz, kullandığı standart komutları bildirmelidir ve sonra bir *. vsct* dosyasındaki yeni komutları, bağlam menülerini, üst düzey menüleri ve araç çubuklarını tanımlar. Yerinde etkinleştirme Düzenleyicisi oluşturursanız, <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> uygulayın ve OLE 2 menü birleştirme kullanmak yerine bir *. vsct* dosyasında düzenleyici için menüleri ve araç çubuklarını tanımlayın.

- Kullanıcı arabiriminde menü komutunun kalabonu engellemek için, yeni komutları oluşturmadan önce IDE 'de var olan komutları kullanmanız gerekir. Paylaşılan komutlar *SharedCmdDef. vsct* ve *ShellCmdDef. vsct*içinde tanımlanır. Bu dosyalar, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] yüklemenizin VisualStudioIntegration\Common\Inc alt dizininde varsayılan olarak yüklenir.

- `ISelectionContainer` hem tek hem de birden çok seçimi ifade edebilir. Seçili her nesne `IDispatch` nesne olarak uygulanır.

- IDE, bir <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> erişilebilen bir hizmet olarak veya <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>aracılığıyla örneklenebilir bir nesne olarak `IOleUndoManager` uygular. Düzenleyiciniz her `Undo` eylemi için `IOleUndoUnit` arabirimini uygular.

- Özel bir düzenleyicinin Otomasyon nesnelerini kullanıma sunabilecekleri iki konum vardır:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Ayrıca bkz.

- [Otomasyon modeline katkıda bulunma](../extensibility/internals/contributing-to-the-automation-model.md)