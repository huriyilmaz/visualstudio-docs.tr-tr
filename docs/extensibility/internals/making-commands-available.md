---
title: Komutları kullanılabilir hale getirme | Microsoft Docs
description: Gecikmeli yükleme, bağlam ve görünürlük kullanılarak VSPackages içindeki Visual Studio IDE 'ye eklenen komutların kullanılabilirliğini nasıl denetleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29f5e5c634c1bf360409e35c87684282a26e8a07
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095218"
---
# <a name="making-commands-available"></a>Komutları kullanılabilir hale getirme

Visual Studio 'ya birden çok VSPackages eklendiğinde, Kullanıcı arabirimi (UI) komutlarla birlikte ortaya çıkabilir. Bu sorunu azaltmaya yardımcı olmak için paketinizi aşağıdaki şekilde programlayabilirsiniz:

- Paketi yalnızca bir Kullanıcı gerektirdiğinde yüklenecek şekilde programlayabilirsiniz.

- Komutları yalnızca tümleşik geliştirme ortamının (IDE) geçerli durumu bağlamında gerekebilecek durumlarda görüntülenecek şekilde programlayabilirsiniz.

## <a name="delayed-loading"></a>Gecikmeli yükleme

Gecikmeli yüklemeyi etkinleştirmenin tipik yolu, komut Kullanıcı arabiriminde görüntülenmek üzere VSPackage tasarlayacağından, bir kullanıcı komutlardan birine tıklaana kadar paketin kendisi yüklenmez. Bunu gerçekleştirmek için,. vsct dosyasında komut bayrakları olmayan komutlar oluşturun.

Aşağıdaki örnek, bir. vsct dosyasındaki bir menü komutunun tanımını gösterir. Bu, şablondaki **menü komutu** seçeneği belirlendiğinde Visual Studio paket şablonu tarafından oluşturulan komuttur.

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

Örnekte, üst grup, `MyMenuGroup` **Araçlar** menüsü gibi üst düzey bir menünün bir alt öğesi ise, komut bu menüde görünür olur, ancak komut bir kullanıcı tarafından tıklanana kadar komutu yürüten paket yüklenmez. Bununla birlikte, arabirimi uygulamak için komutunu programlayarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , komutu içeren menü ilk genişletildiğinde paketin yüklenmesine izin verebilirsiniz.

Gecikmeli yüklemenin de başlangıç performansını iyileştirebileceğini unutmayın.

## <a name="current-context-and-the-visibility-of-commands"></a>Geçerli bağlam ve komutların görünürlüğü

VSPackage komutlarının geçerli durumuna veya şu anda ilgili eylemlere bağlı olarak, VSPackage komutlarını görünür veya gizli olacak şekilde programlayabilirsiniz. Genellikle, arabiriminden yönteminin bir uygulamasını kullanarak, kendi komutlarının durumunu ayarlamak için VSPackage <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 'ı etkinleştirebilirsiniz, ancak bu, kodu yürütebilmesi Için VSPackage 'ın yüklenmesini gerektirir. Bunun yerine, IDE 'yi, paketi yüklemeden komutların görünürlüğünü yönetmek için etkinleştirmenizi öneririz. Bunu yapmak için,. vsct dosyasında komutları bir veya daha fazla özel UI bağlamlarıyla ilişkilendirin. Bu Kullanıcı arabirimi bağlamları, *komut BAĞLAMı GUID*'si olarak BILINEN bir GUID tarafından tanımlanır.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje yükleme veya düzenlemeden oluşturmaya bağlanma gibi kullanıcı eylemlerinden kaynaklanan değişiklikleri izler. Değişiklikler gerçekleştiğinde IDE görünümü otomatik olarak değiştirilir. Aşağıdaki tabloda, izleyen IDE değişikliğinin dört ana bağlamı gösterilmektedir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

| Bağlam türü | Description |
|-------------------------| - |
| Etkin proje türü | Çoğu proje türü için bu `GUID` değer, projeyi uygulayan VSPackage 'un GUID 'si ile aynıdır. Ancak, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projeler proje türünü `GUID` değer olarak kullanır. |
| Etkin pencere | Genellikle, bu, anahtar bağlamaları için geçerli kullanıcı arabirimi bağlamını kuran son etkin belge penceresidir. Bununla birlikte, iç Web tarayıcısına benzer bir anahtar bağlama tablosuna sahip bir araç penceresi de olabilir. HTML Düzenleyicisi gibi çok sekmeli belge pencereleri için her sekmenin farklı bir komut bağlamı vardır `GUID` . |
| Etkin dil hizmeti | Şu anda bir metin düzenleyicisinde görüntülenen dosyayla ilişkili dil hizmeti. |
| Etkin araç penceresi | Açık ve odaklanmış bir araç penceresi. |

Bir beşinci önemli bağlam alanı, IDE 'nin UI durumudur. UI bağlamları, etkin komut bağlamı tarafından `GUID` aşağıdaki gibi tanımlanır:

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

Bu GUID 'Ler, IDE 'nin geçerli durumuna bağlı olarak etkin veya etkin değil olarak işaretlenir. Aynı anda birden çok UI bağlamı etkin olabilir.

### <a name="hide-and-display-commands-based-on-context"></a>Bağlam temelinde komutları gizleme ve görüntüleme

Paketin kendisini yüklemeden IDE 'deki bir paket komutunu gösterebilir veya gizleyebilirsiniz. Bunu yapmak için,, `DefaultDisabled` `DefaultInvisible` ve `DynamicVisibility` komut bayraklarını kullanarak ve bir veya daha fazla [VisibilityItem](../../extensibility/visibilityitem-element.md) öğesini [visibilitykısıtlamalar](../../extensibility/visibilityconstraints-element.md) bölümüne ekleyerek paketin. vsct dosyasında komutunu tanımlayın. Belirtilen bir komut bağlamı `GUID` etkin hale geldiğinde, komut paket yüklenmeden görüntülenir.

### <a name="custom-context-guids"></a>Özel bağlam GUID 'Leri

Uygun bir komut bağlamı GUID 'SI zaten tanımlanmamışsa, VSPackage içinde bir tane tanımlayabilir ve ardından komutlarınızın görünürlüğünü denetlemek için gerektiğinde etkin veya devre dışı olarak programlayabilirsiniz. Hizmetini kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> şunları yapın:

- Bağlam GUID 'Lerini kaydedin (yöntemini çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> ).

- Bağlam durumunu alır `GUID` ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> yöntemini çağırarak).

- Bağlamı açın `GUID` ve kapatın ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> yöntemini çağırarak).

    > [!CAUTION]
    > Diğer VSPackages bunlara bağlı olabileceğinden VSPackage 'ın var olan herhangi bir bağlam GUID 'sinin durumunu etkilemediğinden emin olun.

## <a name="example"></a>Örnek

Aşağıdaki VSPackage komutuna örnek, VSPackage yüklenmeden komut bağlamlarının yönettiği bir komutun dinamik görünürlüğünü gösterir.

Komut, bir çözüm olduğunda etkinleştirilecek ve görüntülenecek şekilde ayarlanır; diğer bir deyişle, aşağıdaki komut bağlamı GUID 'Lerinin her biri etkin olduğunda:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Örnekte, her komut bayrağının ayrı bir [komut bayrağı](../../extensibility/command-flag-element.md) öğesi olduğunu fark edersiniz.

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

Ayrıca, her UI bağlamının aşağıdaki gibi ayrı bir öğede verilmesi gerektiğini de unutmayın `VisibilityItem` .

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
