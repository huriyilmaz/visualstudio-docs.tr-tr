---
title: 'Adım adım kılavuz: Özel Düzenleyiciye Özellik Ekleme | Microsoft Docs'
description: Bu izlenecek yolu kullanarak düzenleyiciyi oluşturduktan sonra özel düzenleyiciye daha fazla özellik ekleme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 73b1eccb945a55011f08347e9b9402976e954ced
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056686"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Adım adım kılavuz: Özel düzenleyiciye özellik ekleme
Özel bir düzenleyici oluşturduktan sonra bu düzenleyiciye daha fazla özellik abilirsiniz.

## <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage için düzenleyici oluşturmak için

1. Visual Studio Package proje şablonunu kullanarak özel bir düzenleyici oluşturun.

     Daha fazla bilgi için [bkz. Adım adım kılavuz: Özel düzenleyici oluşturma.](../extensibility/walkthrough-creating-a-custom-editor.md)

2. Düzenleyicinizin tek bir görünümü veya birden çok görünümü desteklemesi isteyip istediğinize karar verin.

     Yeni Pencere komutunu destekleyen **veya form görünümü** ve kod görünümüne sahip bir düzenleyici, ayrı belge veri nesneleri ve belge görünümü nesneleri gerektirir. Yalnızca tek bir görünümü destekleyen bir düzenleyicide, belge veri nesnesi ve belge görünümü nesnesi aynı nesne üzerinde uygulanabilirsiniz.

     Birden çok görünüm örneği için bkz. [Birden çok belge görünümlerini destekleme.](../extensibility/supporting-multiple-document-views.md)

3. Arabirimini ayarerek bir düzenleyici fabrikası <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> uygulama.

     Daha fazla bilgi için bkz. [Düzenleyici fabrikaları.](/previous-versions/visualstudio/visual-studio-2015/extensibility/editor-factories?preserve-view=true&view=vs-2015)

4. Belge görünümü nesne penceresini yönetmek için düzenleyicinizin yerinde etkinleştirme mi yoksa basitleştirilmiş ekleme mi kullanmak istediğinize karar verin.

     Basitleştirilmiş bir ekleme düzenleyicisi penceresi standart bir belge görünümü barındırırken, yerinde etkinleştirme düzenleyicisi penceresi belge görünümü olarak bir ActiveX veya diğer etkin nesneyi barındırıyor. Daha fazla bilgi için [bkz. Basitleştirilmiş Ekleme](../extensibility/simplified-embedding.md) [ve Yerinde etkinleştirme.](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015)

5. Komutları işlemek <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> için arabirimini uygulama.

6. Belge kalıcılığı ve dış dosya değişikliklerine yanıt sağlama:

    1. Dosyayı kalıcı yapmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> düzenleyicinizin <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> belge veri nesnesine ve ekleyin.

    2. Dış dosya değişikliklerine yanıt vermek için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> ve'i düzenleyicinizin belge veri nesnesine ekleyin.

        > [!NOTE]
        > için `QueryService` bir işaretçi almak için <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> çağrısında `IVsFileChangeEx` bulundu.

7. Kaynak kodu denetimiyle belge düzenleme olaylarını koordine etmek. Şu adımları izleyin:

    1. üzerinde çağırarak `IVsQueryEditQuerySave2` `QueryService` işaretçisini elde <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> etmek.

    2. İlk düzenleme olayı oluştuğunda yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağır.

         Bu yöntem, henüz kullanıma alınmış durumda değilse kullanıcıdan dosyayı kullanıma a yüklemesi istenir. Hataları düzeltmek için "dosya kullanıma alınmış değil" koşullarını işlemeyi mutlaka kullanın.

    3. Benzer şekilde, dosyayı kaydetmeden önce yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> çağırabilirsiniz.

         Bu yöntem, kullanıcıdan dosyayı kaydetmemişse veya son kaydetmeden sonra değiştirdiğinde kaydetmesi istenir.

8. Düzenleyicide **seçilen** metnin özelliklerini görüntülemek için Özellikler penceresini etkinleştirin. Şu adımları izleyin:

    1. Metin <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> seçimi her değişiklikte çağrısı yapın ve uygulamanızı iletir. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>

    2. için `QueryService` bir işaretçi almak için <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> hizmette çağrısı. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>

9. Kullanıcıların düzenleyici ile Araç Kutusu arasında veya dış düzenleyiciler (örneğin, araç kutusu) ve Araç Kutusu arasında öğeleri sürükleyip bırakmalarını **Microsoft Word etkinleştirin.** Şu adımları izleyin:

    1. `IDropTarget`IDE'ye düzenleyicinizin bir bırakma hedefi olduğunu haber olarak uygulamak için düzenleyicinize uygulama.

    2. Düzenleyicinizin <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> Araç Kutusunda öğeleri etkinleştire ve devre dışı bırakana kadar görünümde **arabirimini uygulama.**

    3. ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> `QueryService` arabirimleri <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> için bir işaretçi almak için hizmette uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> çağırma.

         Bu adımlar VSPackage'nizin Araç Kutusuna yeni öğeler **eklemelerini sağlar.**

10. Düzenleyiciniz için başka isteğe bağlı özellikler isteyip istemey karar verin.

    - Düzenleyicinizin bul ve değiştir komutlarını desteklemesini almak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> kullanın.

    - Düzenleyicide bir belge ana hat aracı penceresi kullanmak için `IVsDocOutlineProvider` kullanın.

    - Düzenleyicide bir durum çubuğu kullanmak için, uygulamasına ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> çağrısına `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> çağırarak bir işaretçisi elde etmek için `IVsStatusBar` .

         Örneğin, bir düzenleyici satır/ sütun bilgilerini, seçim modunu (akış / kutu) ve ekleme modunu (ekleme / aşırı saldırı) display olabilir.

    - Düzenleyicinizin komutu desteklemesi için önerilen yöntem OLE geri alma `Undo` yöneticisi modelini kullanmaktır. Alternatif olarak düzenleyicinin komutu doğrudan işlemesi `Undo` de mümkün olabilir.

11. VSPackage GUID'leri, menüler, düzenleyici ve diğer özellikler de dahil olmak üzere kayıt defteri bilgileri oluşturun.

     Aşağıda, bir düzenleyicinin düzgün bir şekilde nasıl kaydedil olduğunu göstermek için *.rgs* dosya betiğinize koyan genel bir kod örneği yer almaktadır.

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

12. Bağlama duyarlı Yardım desteği uygulama.

     Bu adım, düzenleyicideki öğeler için F1 Yardımı ve Dinamik Yardım penceresi desteği sağlamanızı sağlar. Daha fazla bilgi için, [bkz. How to: Provide context for editors](/previous-versions/visualstudio/visual-studio-2015/extensibility/how-to-provide-context-for-editors?preserve-view=true&view=vs-2015).

13. Arabirimini kullanarak düzenleyiciden Otomasyon Nesne Modelini ortaya `IDispatch` çıkarma.

     Daha fazla bilgi için [bkz. Otomasyon Modeline Katkıda Bulunmak.](../extensibility/internals/contributing-to-the-automation-model.md)

## <a name="robust-programming"></a>Güçlü programlama

- IDE yöntemini çağıran düzenleyici örneği <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> oluşturulur. Düzenleyici birden çok görünümü destekliyorsa, `CreateEditorInstance` hem belge verilerini hem de belge görünümü nesnelerini oluşturur. Belge veri nesnesi zaten açıksa, değerine null `punkDocDataExisting` olmayan bir değer `IVsEditorFactory::CreateEditorInstance` geçirildi. Düzenleyici fabrika uygulamanız, mevcut bir belge veri nesnesinin üzerinde uygun arabirimleri sorgular ve uyumlu olup olmadığını belirlemeli. Daha fazla bilgi için, [bkz. Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).

- Basitleştirilmiş ekleme yaklaşımını kullanıyorsanız arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> kullanın.

- Yerinde etkinleştirmeyi kullanmaya karar veriyorsanız aşağıdaki arabirimleri kullanın:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Arabirim, `IOleInPlaceComponent` OLE 2 menü birleştirmeyi önlemek için kullanılır.

   Uygulamanız `IOleCommandTarget` Kes, Kopyala ve **Yapıştır** **gibi** komutları **işletir.** uygulanırken, kendi komut menüsü yapısını tanımlamak için düzenleyicinizin kendi .vsct dosyasını mı gerektirdiğine yoksa tarafından tanımlanan standart komutları uygulayıp `IOleCommandTarget` uygulayamay olduğuna karar  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verin. Düzenleyiciler genellikle IDE'nin menülerini kullanır ve genişletür ve kendi araç çubuklarını tanımlar. Ancak, genellikle bir düzenleyicinin IDE'nin standart komut kümesine ek olarak kendi özel komutlarını tanımlaması gerekir. Düzenleyicinizin kullandığı standart komutları tanımlaması ve *ardından bir .vsct* dosyasındaki yeni komutları, bağlam menülerini, üst düzey menüleri ve araç çubuklarını tanımlaması gerekir. Yerinde etkinleştirme düzenleyicisi ekleyebilirsiniz, OLE 2 menü birleştirme kullanmak yerine <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> *bir .vsct* dosyasında düzenleyicinin menülerini ve araç çubuklarını uygulayın ve tanımlayın.

- Kullanıcı arabiriminde menü komutu kitlesini önlemek için, yeni komutlar keşfetmeden önce IDE'de mevcut komutları kullanabilirsiniz. Paylaşılan komutlar *SharedCmdDef.vsct ve* *ShellCmdDef.vsct içinde tanımlanır.* Bu dosyalar, yüklemenizin VisualStudioIntegration\Common\Inc alt dizinine varsayılan olarak [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] yüklenir.

- `ISelectionContainer` hem tek hem de birden çok seçimi ifade ediyor olabilir. Seçilen her nesne bir nesne olarak `IDispatch` uygulanır.

- IDE, aracılığıyla `IOleUndoManager` örneğilandırilebilen bir veya nesnesi <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> olarak erişilebilen bir hizmet olarak <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> uygulanır. Düzenleyiciniz her eylem `IOleUndoUnit` için `Undo` arabirimini uygulayıyor.

- Özel düzenleyicinin otomasyon nesnelerini ortaya çıkara iki yeri vardır:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Ayrıca bkz.

- [Otomasyon modeline katkıda bulunun](../extensibility/internals/contributing-to-the-automation-model.md)