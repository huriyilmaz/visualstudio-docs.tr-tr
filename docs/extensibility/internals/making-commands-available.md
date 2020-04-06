---
title: Komutları Kullanılabilir Hale Getirme | Microsoft Dokümanlar
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707328"
---
# <a name="making-commands-available"></a>Komutları kullanılabilir hale getirme

Visual Studio'ya birden fazla VSPackages eklendiğinde, kullanıcı arabirimi (UI) komutlarla dolup taştırılabilir. Paketinizi bu sorunu azaltmaya yardımcı olacak şekilde aşağıdaki gibi programlayabilirsiniz:

- Paketi yalnızca bir kullanıcı gerektirdiğinde yüklenecek şekilde programla.

- Paketi, komutlarının yalnızca tümleşik geliştirme ortamının (IDE) geçerli durumu bağlamında gerekli olabilecekleri durumlarda görüntülenecek şekilde programlayın.

## <a name="delayed-loading"></a>Gecikmeli yükleme

Gecikmeli yüklemeyi etkinleştirmenin tipik yolu, KOMUTları Kullanıcı Arabirimi'nde görüntülenecek şekilde VSPackage'ı tasarlamaktır, ancak kullanıcı komutlardan birini tıklayana kadar paketin kendisi yüklenmez. Bunu başarmak için ,.vsct dosyasında komut bayrakları olmayan komutlar oluşturun.

Aşağıdaki örnekte ,vsct dosyasından bir menü komutunun tanımı gösterilmektedir. Bu, şablondaki **Menü Komutu** seçeneği seçildiğinde Visual Studio Package Template tarafından oluşturulan komuttur.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

Örnekte, üst grup, `MyMenuGroup` **Araçlar** menüsü gibi üst düzey bir menünün alt öğesiyse, komut bu menüde görünür, ancak komutu çalıştıran paket, komut kullanıcı tarafından tıklanana kadar yüklenmez. Ancak, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi uygulamak için komutu programlayarak, komutu içeren menü ilk genişletildiğinde paketin yüklenmesini etkinleştirebilirsiniz.

Gecikmiş yüklemenin başlangıç performansını da artırabileceğini unutmayın.

## <a name="current-context-and-the-visibility-of-commands"></a>Geçerli bağlam ve komutların görünürlüğü

VSPackage komutlarını, VSPackage verilerinin geçerli durumuna veya şu anda alakalı olan eylemlere bağlı olarak görünür veya gizli olacak şekilde programlayabilirsiniz. VSPackage'ın komutlarının durumunu, genellikle <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimden yöntemin bir uygulamasını kullanarak ayarlamasını etkinleştirebilirsiniz, ancak bu, kodu yürütebilmek için VSPackage'ın yüklenmesini gerektirir. Bunun yerine, IDE'nin paketi yüklemeden komutların görünürlüğünü yönetmesini etkinleştirmenizi öneririz. Bunu yapmak için ,.vsct dosyasında, komutları bir veya daha fazla özel UI bağlamıyla ilişkilendirin. Bu UI bağlamları *komut bağlamı GUID*olarak bilinen bir GUID tarafından tanımlanır.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proje yükleme veya düzenlemeden binaya gitme gibi kullanıcı eylemlerinden kaynaklanan değişiklikleri izler. Değişiklikler meydana geldikçe, IDE'nin görünümü otomatik olarak değiştirilir. Aşağıdaki tablo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] izleyen IDE değişikliğinin dört ana bağlamını gösterir.

| Bağlam Türü | Açıklama |
|-------------------------| - |
| Etkin Proje Türü | Çoğu proje türü `GUID` için bu değer, projeyi uygulayan VSPackage'ın GUID'i ile aynıdır. Ancak, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projeler değer `GUID` olarak Proje Türünü kullanır. |
| Etkin Pencere | Genellikle, bu anahtar bağlamaları için geçerli UI bağlamını oluşturan son etkin belge penceresidir. Ancak, aynı zamanda iç Web tarayıcısı benzer bir anahtar bağlama tablosu olan bir araç penceresi olabilir. HTML düzenleyicisi gibi çok sekmeli belge pencereleri için `GUID`her sekmefarklı bir komut bağlamı vardır. |
| Aktif Dil Servisi | Şu anda bir metin düzenleyicisinde görüntülenen dosyayla ilişkili dil hizmeti. |
| Etkin Araç Penceresi | Açık ve odaklanmış bir araç penceresi. |

Beşinci ana bağlam alanı IDE'nin UI durumudur. UI bağlamları aşağıdaki gibi, `GUID`etkin komut bağlamı tarafından tanımlanır:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Bu GUID'ler, IDE'nin geçerli durumuna bağlı olarak etkin veya etkin olmayan olarak işaretlenir. Birden çok Ara Bilgi bağlamı aynı anda etkin olabilir.

### <a name="hide-and-display-commands-based-on-context"></a>Komutları bağlama göre gizleme ve görüntüleme

Paketin kendisini yüklemeden IDE'de bir paket komutunu görüntüleyebilir veya gizleyebilirsiniz. Bunu yapmak için, paketin .vsct dosyasındaki komutu `DefaultDisabled`, `DefaultInvisible`, `DynamicVisibility` ve komut bayraklarını kullanarak ve Görünürlük Kısıtlamaları bölümüne bir veya daha fazla [Görünürlük Öğesi](../../extensibility/visibilityitem-element.md) öğesi ekleyerek [tanımlayın.](../../extensibility/visibilityconstraints-element.md) Belirli bir komut `GUID` bağlamı etkin hale geldiğinde, komut paketi yüklemeden görüntülenir.

### <a name="custom-context-guids"></a>Özel bağlam GUIDs

Uygun bir komut bağlamı GUID zaten tanımlanmamışsa, VSPackage'ınızda bir tane tanımlayabilir ve ardından komutlarınızın görünürlüğünü denetlemek için gerektiğinde etkin veya etkin olmayan olarak programlayabilirsiniz. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Hizmeti şu şekilde kullanın:

- İçerik GUID'lerini kaydedin <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (yöntemi arayarak).

- Bir bağlam `GUID` Durumunu alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (yöntemi arayarak).

- Bağlamı `GUID`açıp kapatın <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (yöntemi arayarak).

    > [!CAUTION]
    > VSPackage'ınızın varolan herhangi bir bağlam GUID'in durumunu etkilemediğinden emin olun, çünkü diğer VSPackages'lar bunlara bağlı olabilir.

## <a name="example"></a>Örnek

VSPackage komutunun aşağıdaki örneği, VSPackage'ı yüklemeden komut bağlamları tarafından yönetilen bir komutun dinamik görünürlüğünü gösterir.

Komut etkinleştirilecek ve bir çözüm olduğunda görüntülenecek şekilde ayarlanır; diğer bir şey, aşağıdaki komut bağlamından biri GUID'ler etkin olduğunda:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Örnekte, her komut bayrağının ayrı bir [Komut Bayrağı](../../extensibility/command-flag-element.md) öğesi olduğuna dikkat edin.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Ayrıca, her ui bağlamı aşağıdaki `VisibilityItem` gibi ayrı bir öğe içinde verilmelidir dikkat edin.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çözüm Gezgini araç çubuğuna komut ekleme](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dinamik Olarak Menü Öğeleri Ekleme](../../extensibility/dynamically-adding-menu-items.md)
