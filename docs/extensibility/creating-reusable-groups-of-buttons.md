---
title: Yeniden Kullanılabilir Düğme Grupları Oluşturma | Microsoft Docs
description: Bir menü veya araç çubuğunda birlikte görünen komut koleksiyonu olan bir komut grubu oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5ef9e4c78fcd4bfe22ba6bcffcb2fe41d1a7dda2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057999"
---
# <a name="create-reusable-groups-of-buttons"></a>Yeniden kullanılabilir düğme grupları oluşturma
Komut grubu, bir menü veya araç çubuğunda her zaman birlikte görünen komut koleksiyonudur. Herhangi bir komut grubu, *.vsct* dosyasının CommandPlacements bölümünde farklı üst menülere atanarak yeniden kullanılabilir.

 Komut grupları genellikle düğmeler içerir, ancak başka menüler veya birleşik giriş kutuları da içerebilir.

## <a name="to-create-a-reusable-group-of-buttons"></a>Yeniden kullanılabilir bir düğme grubu oluşturmak için

1. adlı bir VSIX projesi `ReusableButtons` oluşturun. Daha fazla bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Proje açıldığında **ReusableCommand** adlı özel bir komut öğesi şablonu ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne** gidin ve Özel **Komut'ı seçin.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını *ReusableCommand.cs olarak değiştirebilirsiniz.*

3. *.vsct dosyasında* Semboller bölümüne gidin ve proje için grupları ve komutları içeren GuidSymbol öğesini bulun. GuidReusableCommandPackageCmdSet olarak adlandırılmış olmalıdır.

4. Aşağıdaki örnekte olduğu gibi gruba ekleyecek her düğme için bir IDSymbol ekleyin.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Varsayılan olarak, komut öğesi şablonu **MyMenuGroup** adlı bir grup ve her biri için bir IDSymbol girdisi ile birlikte, sizin sağladığınız adı olan bir düğme oluşturur.

5. Gruplar bölümünde, Semboller bölümünde verilenler ile aynı GUID ve KIMLIK özniteliklerine sahip bir Group öğesi oluşturun. Ayrıca, aşağıdaki örnekte olduğu gibi var olan bir grubu veya komut şablonu tarafından sağlanan girişi de kullanabilirsiniz. Bu grup Araçlar **menüsünde** görünür

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Yeniden kullanmak üzere bir düğme grubu oluşturmak için

1. Komutu veya menüyü grup tanımında üst öğe olarak kullanarak veya CommandPlacements bölümünü kullanarak komutu veya menüyü gruba koyarak bir gruba komut veya menü ekleyebilirsiniz.

     Düğmeler bölümünde, grubunuz üst öğe olarak kullanılan bir düğme tanımlayın veya aşağıdaki örnekte gösterildiği gibi paket şablonu tarafından sağlanan düğmeyi kullanın.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Bir düğmenin birden fazla grupta görünmesi gerekirse, CommandPlacements bölümünde bunun için Komutlar bölümünden sonra yerleştirilecek bir giriş oluşturun. CommandPlacement öğesinin GUID ve ID özniteliklerini konumlandırmak istediğiniz düğmenin GUID ve ID öznitelikleriyle eş olacak şekilde ayarlayın ve ardından, aşağıdaki örnekte gösterildiği gibi Üst öğesinin GUID ve KIMLIĞINI hedef grubunkilerle ayarlayın.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Öncelik alanı değeri, komutun yeni komut grubunda konumunu belirler. CommandPlacement öğesinde ayarlanmış olan öncelikler, öğe tanımında ayarlanmış olan öncelikleri geçersiz kılar. Düşük öncelikli değerlere sahip komutlar, daha yüksek öncelikli değerlere sahip komutlar önce görüntülenir. Yinelenen öncelik değerlerine izin verilir, ancak aynı öncelik değerine sahip komutların göreli konumu garanti edilemez çünkü **devenv /setup** komutunun kayıt defterinden son arabirimi oluşturduğu sıra tutarlı olamaz.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Bir menüye yeniden kullanılabilir düğme grubu koymak için

1. bölümünde bir giriş `CommandPlacements` oluşturun. Öğenin GUID ve kimliğini grubunuz için, üst GUID ve kimliği ise hedef `CommandPlacement` konumun GUID'leri olarak ayarlayın.

    CommandPlacements bölümü, Komutlar bölümünün hemen altına yerleştirilebiliyor:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Bir komut grubu birden fazla menüye dahil olabilir. Üst menü sizin oluşturduğunuz, tarafından sağlanan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] *(ShellCmdDef.vsct* veya *SharedCmdDef.vsct* içinde açıklandığı gibi) veya başka bir VSPackage içinde tanımlanan bir menü olabilir. Üst menü sonunda VSPackage tarafından görüntülenen bir kısayol menüsüne veya bir kısayol menüsüne bağlı olduğu sürece üst öğe katmanı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sayısı sınırsızdır.

    Aşağıdaki örnek grubu diğer **düğmelerin Çözüm Gezgini** araç çubuğuna koyar.

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
