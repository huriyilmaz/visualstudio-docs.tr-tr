---
title: Yeniden Kullanılabilir Düğme Grupları Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739469"
---
# <a name="create-reusable-groups-of-buttons"></a>Yeniden kullanılabilir düğme grupları oluşturma
Komut grubu, menüveya araç çubuğunda her zaman birlikte görünen komutlar topluluğudur. Herhangi bir komut *grubu,.vsct* dosyasının Komut Yerleşimleri bölümündeki farklı üst menülere atayarak yeniden kullanılabilir.

 Komut grupları genellikle düğmeler içerir, ancak diğer menüler veya açılan kutular da içerebilir.

## <a name="to-create-a-reusable-group-of-buttons"></a>Yeniden kullanılabilir bir düğme grubu oluşturmak için

1. Adlı `ReusableButtons`bir VSIX projesi oluşturun. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Proje açıldığında, **ReusableCommand**adlı özel bir komut öğesi şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve **Özel Komut'u**seçin. Pencerenin altındaki **Ad** alanında komut dosyası adını *ReusableCommand.cs*olarak değiştirin.

3. *.vsct* dosyasında, Semboller bölümüne gidin ve proje için gruplar ve komutlar içeren GuidSymbol öğesini bulun. GuidReusableCommandPackageCmdSet olarak adlandırılmalıdır.

4. Aşağıdaki örnekte olduğu gibi gruba ekleyeceğiniz her düğme için bir IDSymbol ekleyin.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Varsayılan olarak, komut öğesi şablonu **MyMenuGroup** adında bir grup ve her biri için bir IDSymbol girişi yle birlikte sağladığınız adı içeren bir düğme oluşturur.

5. Gruplar bölümünde, Semboller bölümünde verilenle aynı GUID ve ID özniteliklerine sahip bir Grup öğesi oluşturun. Varolan bir grubu da kullanabilir veya aşağıdaki örnekte olduğu gibi komut şablonu tarafından sağlanan girişi kullanabilirsiniz. Bu grup **Araçlar** menüsünde görünür

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Yeniden kullanmak için bir düğme grubu oluşturmak için

1. Komut veya menü tanımında grubu üst öğe olarak kullanarak veya Komut Yerleşimleri bölümünü kullanarak gruba komut veya menü koyarak bir gruba komut veya menü koyabilirsiniz.

     Düğmeler bölümünde, grubunuzun üst öğesi olarak sahip olduğu bir düğme tanımlayın veya aşağıdaki örnekte gösterildiği gibi paket şablonu tarafından sağlanan düğmeyi kullanın.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Bir düğmebirden fazla grupta görünmesi gerekiyorsa, KomutLar bölümünden sonra yerleştirilmesi gereken Komut Yerleşimleri bölümünde bunun için bir giriş oluşturun. CommandPlacement öğesinin GUID ve ID özniteliklerini, konumlandırmak istediğiniz düğmeyle eşleşecek şekilde ayarlayın ve ardından Aşağıdaki örnekte gösterildiği gibi Üst öğesinin GUID ve Kimliğini hedef grubunkilerle ayarlayın.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Öncelik alanının değeri, komutun yeni komut grubundaki konumunu belirler. Komut Yerleştirme öğesinde ayarlanan öncelikler madde tanımında ayarlananları geçersiz kılar. Daha düşük öncelik değerlerine sahip komutlar, daha yüksek öncelik değerlerine sahip komutların önünde görüntülenir. Yinelenen öncelik değerlerine izin verilir, ancak **devenv /kurulum** komutunun kayıt defterinden son arabirimi oluşturduğu sıra tutarlı olmayabilir, ancak aynı öncelik değerine sahip komutların göreli konumu garanti edilemez.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Menüye yeniden kullanılabilir bir düğme grubu koymak için

1. `CommandPlacements` Bölümde bir giriş oluşturun. Öğenin `CommandPlacement` GUID ve Kimliğini grubunuzunkilerle ayarlayın ve üst GUID ve Kimliğini hedef konumunkilere ayarlayın.

    Komut Yerleşimleri bölümü Komutlar bölümünden hemen sonra yerleştirilmelidir:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Bir komut grubu birden fazla menüye eklenebilir. Üst menü oluşturduğunuz, *(ShellCmdDef.vsct veya SharedCmdDef.vsct'de* açıklandığı gibi) tarafından *SharedCmdDef.vsct* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sağlanan veya başka bir VSPackage'da tanımlanan bir menü olabilir. Üst menü sonunda vspackage tarafından görüntülenen bir kısayol menüsüne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya bağlı olduğu sürece ebeveynlik katmanlarının sayısı sınırsızdır.

    Aşağıdaki örnek, grubu **Çözüm Gezgini** araç çubuğuna, diğer düğmelerin sağında yer alır.

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
