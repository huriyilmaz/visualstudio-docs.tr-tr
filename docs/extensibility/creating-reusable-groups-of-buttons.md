---
title: Yeniden kullanılabilir düğme grupları oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 477014ed77b60821ad191ba6842999be6f528fee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903651"
---
# <a name="create-reusable-groups-of-buttons"></a>Yeniden kullanılabilir düğme grupları oluşturma
Komut grubu, her zaman bir menü veya araç çubuğunda birlikte görünen komutların bir koleksiyonudur. Herhangi bir komut grubu, *. vsct* dosyasının CommandPlacements bölümünde farklı üst menülere atayarak yeniden kullanılabilir.

 Komut grupları genellikle düğmeler içerir, ancak diğer menüleri veya Birleşik giriş kutularını da içerebilir.

## <a name="to-create-a-reusable-group-of-buttons"></a>Yeniden kullanılabilir düğme grubu oluşturmak için

1. Adlı bir VSıX projesi oluşturun `ReusableButtons` . Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Proje açıldığında, **ReusableCommand**adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *ReusableCommand.cs*olarak değiştirin.

3. *. Vsct* dosyasında, semboller bölümüne gidin ve proje için grupları ve komutları Içeren GuidSymbol öğesini bulun. Bu, guidReusableCommandPackageCmdSet olarak adlandırılmalıdır.

4. Aşağıdaki örnekte olduğu gibi, gruba ekleyeceğiniz her düğme için bir IDSymbol ekleyin.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Varsayılan olarak, komut öğesi şablonu **MyMenuGroup** adlı bir grup ve her biri Için bir IDSymbol girişi ile birlikte verdiğiniz adı içeren bir düğme oluşturur.

5. Gruplar bölümünde, semboller bölümünde verilen olanlarla aynı GUID ve ID özniteliklerine sahip bir Grup öğesi oluşturun. Ayrıca, aşağıdaki örnekte olduğu gibi, var olan bir grubu kullanabilir veya komut şablonu tarafından sağlanmış girişi kullanabilirsiniz. Bu grup, **Araçlar** menüsünde görünür

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Yeniden kullanmak üzere bir düğme grubu oluşturmak için

1. Bir komutu veya menüyü, komutun veya menünün tanımında bir üst öğe olarak kullanarak ya da komutu ya da menüyü, CommandPlacements bölümünü kullanarak grubuna yerleştirerek ekleyebilirsiniz.

     Düğmeler bölümünde, kendi üst öğesi olan grubunuz olan bir düğmeyi tanımlayın veya aşağıdaki örnekte gösterildiği gibi paket şablonu tarafından verilen düğmeyi kullanın.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Bir düğme birden fazla grupta yer alıyorsa, komut bölümünün ardından yerleştirilmesi gereken CommandPlacements bölümünde bir giriş oluşturun. Commandyerleştirme öğesinin GUID ve ID özniteliklerini konumlandırmak istediğiniz düğmeden eşleşecek şekilde ayarlayın ve ardından üst öğesinin GUID ve KIMLIĞINI aşağıdaki örnekte gösterildiği gibi hedef gruba göre ayarlayın.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Öncelik alanının değeri, yeni komut grubundaki komutun konumunu belirler. Commandyerleştirme öğesinde ayarlanan öncelikler, öğe tanımındaki kümeyi geçersiz kılar. Düşük öncelik değerleri olan komutlar, daha yüksek öncelik değerleri olan komutlardan önce görüntülenir. Yinelenen öncelik değerlerine izin verilir, ancak **devenv/setup** komutunun, kayıt defterinden son arabirimi oluşturduğu sıra tutarlı olmayabilir, ancak aynı öncelik değerine sahip komutların göreli konumu garanti edilemez.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Bir menüye yeniden kullanılabilir düğme grubu koymak için

1. Bölümünde bir giriş oluşturun `CommandPlacements` . Öğenin GUID ve KIMLIĞINI `CommandPlacement` grubunuza göre ayarlayın ve üst GUID ve kimliği hedef konumlarından ayarlayın.

    CommandPlacements bölümü, komutlar bölümünden hemen sonra yerleştirilmelidir:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Bir komut grubu, birden fazla menüye eklenebilir. Ana menü, oluşturduğunuz biri olan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ( *ShellCmdDef. vsct* veya *SharedCmdDef. vsct*içinde açıklandığı gibi) ya da başka bir VSPackage içinde tanımlanmış bir tane olabilir. Üst menü sonunda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya VSPackage tarafından görüntülenen bir kısayol menüsüne bağlı olduğu sürece, eklenen katmanların sayısı sınırsızdır.

    Aşağıdaki örnek, grubu **Çözüm Gezgini** araç çubuğuna diğer düğmelerin sağına koyar.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
