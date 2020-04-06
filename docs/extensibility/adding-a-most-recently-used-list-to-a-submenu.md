---
title: Alt Menüye En Son Kullanılan Liste Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740295"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Alt menüye en son kullanılan liste ekleme
Bu gözden geçirme, bir [menüye alt menü ekle'deki](../extensibility/adding-a-submenu-to-a-menu.md)gösterilere göre oluşturur ve bir alt menüye dinamik bir liste nin nasıl ekleyeceğini gösterir. Dinamik liste, en son kullanılan (MRU) listesini oluşturmak için temel oluşturur.

Dinamik menü listesi menüdeki yer tutucuyla başlar. Menü her gösterildiğinde, Visual Studio entegre geliştirme ortamı (IDE) yer tutucuda gösterilmesi gereken tüm komutları VSPackage'dan ister. Menüde herhangi bir yerde dinamik bir liste oluşabilir. Ancak, dinamik listeler genellikle alt menülerde veya menülerin altlarında kendileri tarafından depolanır ve görüntülenir. Bu tasarım desenlerini kullanarak, menüdeki diğer komutların konumunu etkilemeden dinamik komut listesinin genişlemesini ve daraltılmasını sağlarsınız. Bu gözden geçirme de, dinamik MRU listesi varolan bir alt menünün alt menüsünün alt kısmında görüntülenir ve alt menünün geri kalanından bir satırla ayrılır.

Teknik olarak, dinamik bir liste araç çubuğuna da uygulanabilir. Ancak, kullanıcı değiştirmek için belirli adımlar atmadığı sürece bir araç çubuğu değişmeden kalması gerektiğinden, bu kullanımı öneriz.

Bu izne, her biri seçildiğinde siparişlerini değiştiren dört öğeden oluşan bir MRU listesi oluşturur (seçili öğe listenin en üstüne taşınır).

Menüler ve *.vsct* dosyaları hakkında daha fazla bilgi için [Komutlar, menüler ve araç çubuklarına](../extensibility/internals/commands-menus-and-toolbars.md)bakın.

## <a name="prerequisites"></a>Ön koşullar
Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="create-an-extension"></a>Uzantı oluşturma

- Aşağıdaki yordamlarda değiştirilen alt menüyü oluşturmak [için bir alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md) yordamlarını izleyin.

  Bu gözden geçirme işlemindeki yordamlar, VSPackage'ın adının [Visual Studio menü çubuğuna menü ekle'de](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)kullanılan ad olduğunu `TopLevelMenu`varsayar.

## <a name="create-a-dynamic-item-list-command"></a>Dinamik madde listesi komutu oluşturma

1. *Açık TestCommandPackage.vsct*.

2. `Symbols` GuidTestCommandPackageCmdSet adlı `GuidSymbol` düğümdeki bölümde, `MRUListGroup` grup ve `cmdidMRUList` komut için aşağıdaki gibi sembolü ekleyin.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Bölüme, `Groups` varolan grup girdisi sonra bildirilen grup ekleyin.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. `Buttons` Bölümde, varolan düğme girişlerden sonra yeni bildirilen komutu temsil edecek bir düğüm ekleyin.

    ```csharp
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"
        type="Button" priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />
        <CommandFlag>DynamicItemStart</CommandFlag>
        <Strings>
            <CommandName>cmdidMRUList</CommandName>
            <ButtonText>MRU Placeholder</ButtonText>
        </Strings>
    </Button>
    ```

    Bayrak, `DynamicItemStart` komutun dinamik olarak oluşturulmasını sağlar.

5. Projeyi oluşturun ve yeni komutun ekranını sınamak için hata ayıklamaya başlayın.

    **TestMenu** menüsünde, yeni alt menü, **Alt Menü**, yeni komut, **MRU Placeholder**görüntülemek için tıklayın. Bir sonraki yordamda dinamik bir MRU komut listesi uygulandıktan sonra, bu komut etiketi alt menü her açıldığında bu listeyle değiştirilir.

## <a name="filling-the-mru-list"></a>MRU Listesini Doldurma

1. *TestCommandPackageGuids.cs,* `TestCommandPackageGuids` sınıf tanımında varolan komut işlemisonra si

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. *TestCommand.cs* aşağıdaki kullanarak deyimi ekleyin.

    ```csharp
    using System.Collections;
    ```

3. Son AddCommand çağrısından sonra TestKomutu oluşturucuya aşağıdaki kodu ekleyin. Daha `InitMRUMenu` sonra tanımlanacak

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. TestKomutu sınıfına aşağıdaki kodu ekleyin. Bu kod, MRU listesinde gösterilecek öğeleri temsil eden dizeleri listesini başlatılmasını.

    ```csharp
    private int numMRUItems = 4;
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;
    private ArrayList mruList;

    private void InitializeMRUList()
    {
        if (null == this.mruList)
        {
            this.mruList = new ArrayList();
            if (null != this.mruList)
            {
                for (int i = 0; i < this.numMRUItems; i++)
                {
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,
                        "Item {0}", i + 1));
                }
            }
        }
    }
    ```

5. Yöntemden `InitializeMRUList` sonra, `InitMRUMenu` yöntemi ekleyin. Bu, MRU liste menü komutlarını başharfe getirir.

    ```csharp
    private void InitMRUMenu(OleMenuCommandService mcs)
    {
        InitializeMRUList();
        for (int i = 0; i < this.numMRUItems; i++)
        {
            var cmdID = new CommandID(
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);
            var mc = new OleMenuCommand(
                new EventHandler(OnMRUExec), cmdID);
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);
            mcs.AddCommand(mc);
        }
    }
    ```

    MRU listesindeki her olası öğe için bir menü komut nesnesi oluşturmanız gerekir. IDE, mru listesindeki her öğe için `OnMRUQueryStatus` yöntemi, başka öğe olmayana kadar çağırır. Yönetilen kodda, IDE'nin başka öğe olmadığını bilmesinin tek yolu önce tüm olası öğeleri oluşturmaktır. İsterseniz, menü komutu oluşturulduktan sonra kullanarak `mc.Visible = false;` ilk başta görünmeyen ek öğeleri işaretleyebilirsiniz. Bu öğeler daha sonra `mc.Visible = true;` `OnMRUQueryStatus` yöntem kullanılarak görünür hale getirilebilir.

6. Yöntemden `InitMRUMenu` sonra, aşağıdaki `OnMRUQueryStatus` yöntemi ekleyin. Bu, her MRU öğesi için metni ayarlayan işleyicidir.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Yöntemden `OnMRUQueryStatus` sonra, aşağıdaki `OnMRUExec` yöntemi ekleyin. Bu, bir MRU öğesi seçmek için işleyicisi. Bu yöntem, seçili öğeyi listenin en üstüne taşır ve sonra seçili öğeyi bir ileti kutusunda görüntüler.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
                for (int i = MRUItemIndex; i > 0; i--)
                {
                    this.mruList[i] = this.mruList[i - 1];
                }
                this.mruList[0] = selection;
                System.Windows.Forms.MessageBox.Show(
                    string.Format(CultureInfo.CurrentCulture,
                                  "Selected {0}", selection));
            }
        }
    }

    ```

## <a name="testing-the-mru-list"></a>MRU listesini test etme

1. Projeyi oluşturun ve hata ayıklamaya başlayın.

2. **TestMenu** menüsünde, **TestKomutunu Çağır'ı**tıklatın. Bunu yaparken, komutun seçildiğini gösteren bir ileti kutusu görüntülenir.

    > [!NOTE]
    > Bu adım, VSPackage'ı MRU listesini yüklemeye ve doğru şekilde görüntülemeye zorlamak için gereklidir. Bu adımı atlarsanız, MRU listesi görüntülenmez.

3. Test **Menüsü** menüsünde **Alt Menü'ye**tıklayın. Alt menünün sonunda, bir ayırıcının altında dört öğeden oluşan bir liste görüntülenir. **Öğe 3'e**tıkladığınızda, bir ileti kutusu görünmeli ve metni görüntülemeli, **Seçili Öğe 3**. (Dört öğenin listesi görüntülenmiyorsa, önceki adımdaki yönergeleri izlediğinizi emin olun.)

4. Alt menüyü yeniden açın. Madde **3'ün** artık listenin en üstünde olduğunu ve diğer öğelerin bir konumdan aşağı itildiğini unutmayın. **Madde 3'e** yeniden tıklayın ve ileti kutusunun hala **Seçili Öğe 3'ün**görüntülendiğini ve bu da metnin komut etiketiyle birlikte yeni konuma doğru şekilde taşındığını gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dinamik menü öğeleri ekleme](../extensibility/dynamically-adding-menu-items.md)
