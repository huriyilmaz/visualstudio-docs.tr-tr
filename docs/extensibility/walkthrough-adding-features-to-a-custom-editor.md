---
title: 'İzleme: Özel Bir Düzenleyiciye Özellikler Ekleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65ef0edf76780ba7c8b6f5d9347195c286bec466
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649838"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>İzole: Özel bir düzenleyiciye özellikler ekleme
Özel bir düzenleyici oluşturduktan sonra, daha fazla özellik ekleyebilirsiniz.

## <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage için editör oluşturmak için

1. Visual Studio Package proje şablonu kullanarak özel bir düzenleyici oluşturun.

     Daha fazla bilgi için [Walkthrough: Özel bir düzenleyici oluşturun.](../extensibility/walkthrough-creating-a-custom-editor.md)

2. Düzenleyicinizin tek bir görünümü mü yoksa birden çok görünümü mi desteklemesini istediğinize karar verin.

     **Yeni Pencere** komutunu destekleyen veya form görünümü ve kod görünümüne sahip bir düzenleyici, ayrı belge veri nesneleri ve belge görünümü nesneleri gerektirir. Yalnızca tek bir görünümü destekleyen bir düzenleyicide, belge veri nesnesi ve belge görünümü nesnesi aynı nesne üzerinde uygulanabilir.

     Birden çok görünüm örneği için [bkz.](../extensibility/supporting-multiple-document-views.md)

3. Arabirimi kurarak bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> düzenleyici fabrikası uygulayın.

     Daha fazla bilgi için [Editör fabrikalarına](/visualstudio/extensibility/editor-factories?view=vs-2015)bakın.

4. Düzenleyicinizin belge görünümü nesnesi penceresini yönetmek için yerinde etkinleştirme mi yoksa basitleştirilmiş katıştırma mı kullanacağına karar verin.

     Basitleştirilmiş katıştırma düzenleyicisi penceresi standart bir belge görünümü barındırırken, yerinde etkinleştirme düzenleyicisi penceresi belge görünümü nde ActiveX denetimini veya diğer etkin nesneyi barındırır. Daha fazla bilgi için, [Basitleştirilmiş Katıştırma](../extensibility/simplified-embedding.md) ve [Yerinde etkinleştirme'ye](/visualstudio/misc/in-place-activation?view=vs-2015)bakın.

5. Komutları <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> işlemek için arabirimi uygulayın.

6. Belge kalıcılığı ve dış dosya değişikliklerine yanıt sağlama:

    1. Dosyayı devam ettirmek için, düzenleyicinizin belge veri nesnesini uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> uygulayın.

    2. Harici dosya değişikliklerine yanıt <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> vermek için düzenleyicinizin belge veri nesnesini uygulayın ve uygulayın.

        > [!NOTE]
        > Bir `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> işaretçi almak `IVsFileChangeEx`için çağırın.

7. Kaynak kodu denetimi ile belge düzenle olaylarını koordine edin. Şu adımları uygulayın:

    1. Arayarak `IVsQueryEditQuerySave2` `QueryService` bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>alın.

    2. İlk edit olayı oluştuğunda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemi arayın.

         Bu yöntem, kullanıcıdan dosyayı kullanıma almamışsa dosyayı kullanıma almalarını ister. Hataları önlemek için "dosya kullanıma alınmadı" koşulunu işlediğinden emin olun.

    3. Benzer şekilde, dosyayı kaydetmeden <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> önce yöntemi arayın.

         Bu yöntem, kullanıcıdan dosya kaydedilmemişse veya son kaydedilmeden sonra değiştirildiyse dosyayı kaydetmesini ister.

8. Editörde seçilen metnin özelliklerini görüntülemek için **Özellikler** penceresinin etkinleştirin. Şu adımları uygulayın:

    1. Metin <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> seçimi her değiştiğinde, uygulamanızdan <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>geçerek arayın.

    2. Bir `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> işaretçi almak için <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>hizmeti arayın.

9. Kullanıcıların öğeleri düzenleyici ve **Araç Kutusu**arasında veya dış düzenleyiciler (Microsoft Word gibi) ve **Araç Kutusu**arasında sürüklemesine ve bırakmasını etkinleştirin. Şu adımları uygulayın:

    1. IDE'yi düzenleyicinizin bir hedef olduğu konusunda uyarmak için düzenleyicinizi uygulayın. `IDropTarget`

    2. Düzenleyicinizin <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> **Toolbox'taki**öğeleri etkinleştirip devre dışı kabilmesi için görünümdeki arabirimi uygulayın.

    3. Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> ve `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> hizmet çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> bir işaretçi ve arabirimler için bir işaretçi elde etmek için.

         Bu adımlar, VSPackage'ınızın Araç **Kutusuna**yeni öğeler eklemesini sağlar.

10. Düzenleyiciniz için başka isteğe bağlı özellikler isteyip istemediğinize karar verin.

    - Düzenleyicinizin bula komutları desteklemesini ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>değiştirmesini istiyorsanız, uygulayın.

    - Düzenleyicinizde belge anahat araç penceresi kullanmak istiyorsanız, `IVsDocOutlineProvider`uygulayın.

    - Düzenleyicinizde bir durum çubuğu kullanmak istiyorsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> bir `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> işaretçi almak `IVsStatusBar`için uygulayın ve arayın.

         Örneğin, bir düzenleyici satır / sütun bilgilerini, seçim modunu (akış / kutu) ve ekleme modunu (ekleme / overstrike) görüntüleyebilir.

    - Düzenleyicinizin komutu desteklemesini `Undo` istiyorsanız, önerilen yöntem OLE geri alma yöneticisi modelini kullanmaktır. Alternatif olarak, düzenleyicinin komutu `Undo` doğrudan işlemesini sağlayabilirsiniz.

11. VSPackage, menüler, düzenleyici ve diğer özellikler için GUID'ler de dahil olmak üzere kayıt defteri Bilgileri oluşturun.

     Aşağıda, bir düzenleyicinin düzgün bir şekilde nasıl kaydolacağınıgöstermek için *.rgs* dosya komut dosyanıza koyacağınız genel bir kod örneği verilmiştir.

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

12. İçeriğe duyarlı Yardım desteği uygulayın.

     Bu adım, düzenleyicinizdeki öğeler için F1 Yardım ve Dinamik Yardım penceresi desteği sağlamanıza olanak tanır. Daha fazla bilgi için [bkz: Editörler için bağlam sağlayın.](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015)

13. `IDispatch` Arabirimi uygulayarak düzenleyicinizden bir Otomasyon Nesnemodeli açığa çıkar.

     Daha fazla bilgi için bkz: [Otomasyon Modeline Katkıda Bulunmak.](../extensibility/internals/contributing-to-the-automation-model.md)

## <a name="robust-programming"></a>Sağlam programlama

- IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi aradığında düzenleyici örneği oluşturulur. Düzenleyici birden çok görünümü `CreateEditorInstance` destekliyorsa, hem belge verilerini hem de belge görünümü nesnelerini oluşturur. Belge veri nesnesi zaten açıksa, `punkDocDataExisting` `IVsEditorFactory::CreateEditorInstance`null olmayan bir değer . Düzenleyici fabrika uygulamanız, varolan bir belge veri nesnesi üzerinde uygun arabirimleri sorgulayarak uyumlu olup olmadığını belirlemelidir. Daha fazla bilgi için bkz: [Birden Çok Belge Görüntülemelerini Destekleme.](../extensibility/supporting-multiple-document-views.md)

- Basitleştirilmiş katıştırma yaklaşımını kullanıyorsanız, arabirimi uygulayın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>

- Yerinde etkinleştirme kullanmaya karar verirseniz, aşağıdaki arabirimleri uygulayın:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Arabirim, `IOleInPlaceComponent` OLE 2 menüsünün birleşmesini önlemek için kullanılır.

   Uygulamanız `IOleCommandTarget` **Kesme,** **Kopyalama**ve **Yapıştır**gibi komutları işler. Uygularken, düzenleyicinizin kendi komut menüsü yapısını tanımlamak için kendi *.vsct* dosyasını gerektirip [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gerektirmediğine veya '' tarafından tanımlanan standart komutları uygulayıp uygulayamayacağına karar verin. `IOleCommandTarget` Genellikle, editörler IDE menülerini kullanır ve genişletir ve kendi araç çubuklarını tanımlar. Ancak, bir düzenleyicinin IDE'nin standart komut kümesini kullanmanın yanı sıra kendi özel komutlarını tanımlaması genellikle gereklidir. Düzenleyiciniz kullandığı standart komutları bildirmeli ve ardından *.vsct* dosyasında yeni komutları, bağlam menülerini, üst düzey menüleri ve araç çubuklarını tanımlamalıdır. Yerinde etkinleştirme düzenleyicisi oluşturursanız, OLE 2 menüsü birleştirme yerine <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> *.vsct* dosyasında düzenleyicinin menülerini ve araç çubuklarını uygulayın ve tanımlayın.

- UI'de menü komutlarının kalabalıklanmasını önlemek için, yeni komutlar icat etmeden önce IDE'deki varolan komutları kullanmanız gerekir. Paylaşılan komutlar *SharedCmdDef.vsct* ve *ShellCmdDef.vsct'de*tanımlanır. Bu dosyalar varsayılan olarak yüklemenizin [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VisualStudioIntegration\Common\Inc alt dizininde yüklenir.

- `ISelectionContainer`hem tek hem de birden çok seçimi ifade edebilir. Seçili her nesne bir `IDispatch` nesne olarak uygulanır.

- IDE, bir `IOleUndoManager` <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> veya bir nesne den <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>erişilebilen bir hizmet olarak uygular. Düzenleyiciniz her `Undo` `IOleUndoUnit` eylem için arabirimi uygular.

- Özel bir düzenleyicinin otomasyon nesnelerini ortaya çıkarabileceği iki yer vardır:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Ayrıca bkz.

- [Otomasyon modeline katkıda bulunmak](../extensibility/internals/contributing-to-the-automation-model.md)
