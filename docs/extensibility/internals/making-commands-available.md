---
title: Komutları Kullanılabilir Hale | Microsoft Docs
description: Gecikmeli yükleme, bağlam ve görünürlük kullanarak VSPackage'larda Visual Studio IDE'ye eklenen komutların kullanılabilirliğini denetlemeyi öğrenin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c92d9b34c669f5de4df8b9bd42cfb9e9e53996e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626102"
---
# <a name="making-commands-available"></a>Komutları kullanılabilir yapma

Kullanıcı arabirimine birden çok VSPackage Visual Studio kullanıcı arabirimi (UI) komutlarıyla aşırı kalabalık hale geliyor olabilir. Bu sorunu azaltmaya yardımcı olmak için paketinizi aşağıdaki gibi programabilirsiniz:

- Paketi yalnızca bir kullanıcı gerektirdiğinde yüklenecek şekilde programla.

- Paketi, komutlarının yalnızca tümleşik geliştirme ortamının (IDE) geçerli durumu bağlamında gerekli olması gerektiğinde görüntülenecek şekilde programla.

## <a name="delayed-loading"></a>Gecikmeli yükleme

Gecikmeli yüklemeyi etkinleştirmenin tipik yolu VSPackage'ın komutlarının kullanıcı arabiriminde görüntülenebilir ancak kullanıcı komutlardan birini tıklayana kadar paketin kendisi yüklenmez. Bunu gerçekleştirmek için .vsct dosyasında komut bayrakları olan komutlar oluşturun.

Aşağıdaki örnek, bir .vsct dosyasından menü komutunun tanımını gösterir. Bu, şablonda Menü Komutu seçeneği Visual Studio Paket Şablonu **tarafından** oluşturulan komutdur.

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

Örnekte, üst grup , Araçlar menüsü gibi üst düzey bir menenin alt öğesi ise, komut bu menüde görünür, ancak komutu yürüten paket, komut bir kullanıcı tarafından tıklanmazsa `MyMenuGroup` yüklenmez.  Ancak, komutunu arabirimini uygulayacak şekilde programlaarak, komutu içeren menü ilk kez genişletilirken <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> paketin yüklenmelerini etkinleştirebilirsiniz.

Gecikmeli yüklemenin başlangıç performansını da geliştirebilir.

## <a name="current-context-and-the-visibility-of-commands"></a>Geçerli bağlam ve komutların görünürlüğü

VSPackage verilerinin geçerli durumuna veya o anda ilgili olan eylemlere bağlı olarak VSPackage komutlarını görünür veya gizli olacak şekilde programabilirsiniz. VSPackage'ın komutlarının durumunu ayarlamasını etkinleştirmek için genellikle arabiriminden yönteminin bir uygulamasını kullanabilirsiniz, ancak bunun için vsPackage'ın kodu yürütemeden önce <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> yüklenmiş olması gerekir. Bunun yerine, paketi yüklemeden komutların görünürlüğünü yönetmek için IDE'yi etkinleştirmenizi öneririz. Bunu yapmak için .vsct dosyasındaki komutları bir veya daha fazla özel kullanıcı arabirimi bağlamıyla ilişkilendirmek. Bu UI bağlamları, komut bağlamı GUID'si olarak bilinen bir *GUID ile tanımlanır.*

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , bir projeyi yükleme veya düzenlemeden binaya devam gibi kullanıcı eylemlerinden elde edilen değişiklikleri izler. Değişiklikler oluştuğunda, IDE'nin görünümü otomatik olarak değiştirilir. Aşağıdaki tabloda, izleyen IDE değişikliğinin dört ana [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bağlamını gösterir.

| Bağlam Türü | Description |
|-------------------------| - |
| Etkin Project Türü | Çoğu proje türü için `GUID` bu değer, projeyi uygulayan VSPackage GUID değeriyle aynıdır. Ancak projeler [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] değer olarak Project Türü `GUID` kullanır. |
| Etkin Pencere | Genellikle bu, anahtar bağlamaları için geçerli kullanıcı arabirimi bağlamını kuran son etkin belge penceresidir. Ancak, iç Web tarayıcısına benzeyen bir anahtar bağlama tablosuna sahip bir araç penceresi de olabilir. HTML düzenleyicisi gibi çok sekmeli belge pencerelerinin her sekmesi farklı bir komut bağlamına `GUID` sahiptir. |
| Etkin Dil Hizmeti | Şu anda bir metin düzenleyicisinde görüntülenen dosyayla ilişkili dil hizmeti. |
| Etkin Araç Penceresi | Açık ve odağı olan bir araç penceresi. |

Beşinci ana bağlam alanı, IDE'nin kullanıcı arabirimi durumudır. Kullanıcı arabirimi bağlamları, etkin komut bağlamları `GUID` tarafından aşağıdaki gibi tanımlanır:

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

Bu GUID'ler IDE'nin geçerli durumuna bağlı olarak etkin veya etkin değil olarak işaretlenir. Aynı anda birden çok kullanıcı arabirimi bağlamı etkin olabilir.

### <a name="hide-and-display-commands-based-on-context"></a>Bağlama göre komutları gizleme ve görüntüleme

Paketin kendisini yüklemeden IDE'de bir paket komutunu görüntüleniyor veya gizleyebilirsiniz. Bunu yapmak için , ve komut bayraklarını kullanarak ve `DefaultDisabled` `DefaultInvisible` `DynamicVisibility` [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) bölümüne bir veya daha fazla [VisibilityItem](../../extensibility/visibilityitem-element.md) öğeleri ekleyerek komutunu paketin .vsct dosyasında tanımlayın. Belirtilen komut bağlamı etkin `GUID` hale geldiğinde, komut paketi yüklemeden görüntülenir.

### <a name="custom-context-guids"></a>Özel bağlam GUID'leri

Uygun bir komut bağlamı GUID'si önceden tanımlanmamışsa, VSPackage içinde bir tane tanımlayabilir ve komutlarınızı görünürlüğünü kontrol etmek için gerektiğinde etkin veya etkin değil olarak programabilirsiniz. Hizmeti kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> şunları yapmak için:

- Bağlam GUID'lerini kaydetme (yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> çağırarak).

- Bir bağlamın durumunu alır `GUID` (yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> çağırarak).

- Bağlamları `GUID` açma ve kapatma (yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> çağırarak).

    > [!CAUTION]
    > Diğer VSPackage'lar bağımlı olduğundan VSPackage'nizin mevcut bağlam GUID'lerinin durumunu etkilemey olduğundan emin olun.

## <a name="example"></a>Örnek

Aşağıdaki VSPackage komutu örneği, VSPackage'ın yüklenmesine gerek kalmadan komut bağlamları tarafından yönetilen bir komutun dinamik görünürlüğünü açıklar.

Komut, etkin olarak ayarlanır ve bir çözüm mevcut olduğunda görüntülenir; diğer bir ifadeyle, aşağıdaki komut bağlamı GUID'lerinden biri etkin olduğunda:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Örnekte, her komut bayrağının ayrı bir Komut Bayrağı öğesi [olduğunu fark](../../extensibility/command-flag-element.md) vardır.

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

Ayrıca her kullanıcı arabirimi bağlamının aşağıdaki gibi ayrı bir öğede `VisibilityItem` verilmesi gerektiğini de fark edersiniz.

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

- [Araç çubuğuna komut Çözüm Gezgini ekleme](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dinamik Olarak Menü Öğeleri Ekleme](../../extensibility/dynamically-adding-menu-items.md)
