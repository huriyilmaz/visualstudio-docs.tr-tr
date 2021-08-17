---
title: Alt menüye en son kullanılan bir liste ekleme | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamındaki (ıde) bir alt menüye en son kullanılan menü komutlarını içeren dinamik bir liste eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71c649d9eeb66b67cde133bef6a525427c618209
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035338"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Alt menüye en son kullanılan bir liste ekleme
Bu izlenecek yol, [bir menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md)ve bir alt menüye nasıl dinamik bir liste ekleneceğini gösterir. Dinamik liste, en son kullanılanlar (MRU) listesini oluşturma temelini oluşturur.

Dinamik menü listesi, bir menüdeki yer tutucu ile başlar. menü her gösterildiğinde, Visual Studio tümleşik geliştirme ortamı (ıde), yer tutucuya gösterilmesi gereken tüm komutlar için vspackage ister. Dinamik bir liste, bir menü üzerinde herhangi bir yerde gerçekleşebilir. Bununla birlikte, dinamik listeler genellikle alt menülerde veya menülere göre kendi alt menülerinde depolanır ve görüntülenir. Bu tasarım düzenlerini kullanarak, menüdeki diğer komutların konumunu etkilemeden genişletmek ve sözleşme yapmak için dinamik komut listesini etkinleştirirsiniz. Bu kılavuzda, dinamik MRU listesi, alt menünün geri kalanından bir çizgi ile ayrılmış olan mevcut bir alt menünün altında görüntülenir.

Teknik olarak, dinamik bir liste bir araç çubuğuna da uygulanabilir. Ancak, Kullanıcı bunu değiştirmek için belirli adımlar almadığı takdirde bir araç çubuğunun değişmeden kalması gerektiğinden bu kullanım yaptık.

Bu izlenecek yol, her birinin seçildiği her seferinde (seçili öğe listenin en üstüne gider), sıralarını değiştiren dört öğenin MRU listesini oluşturur.

Menüler ve *. vsct* dosyaları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Önkoşullar
bu yönergeyi izlemek için Visual Studio SDK 'sını yüklemelisiniz. daha fazla bilgi için bkz. [SDK Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Uzantı oluşturma

- Aşağıdaki yordamlarda değiştirilen alt menüyü oluşturmak için [menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md) içindeki yordamları izleyin.

  bu yönergedeki yordamlar, `TestCommand` [Visual Studio menü çubuğuna bir menü eklemek için](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)kullanılan ad olan vspackage adının olduğunu varsayar.

## <a name="create-a-dynamic-item-list-command"></a>Dinamik öğe listesi komutu oluştur

1. *TestCommandPackage. vsct* öğesini açın.

2. `Symbols`Bölümünde, `GuidSymbol` Guıdtestcommandpackagecmdset adlı düğümde, `MRUListGroup` Grup ve komut için sembolü `cmdidMRUList` aşağıdaki gibi ekleyin.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. `Groups`Bölümünde, varolan Grup girişlerinden sonra, belirtilen grubu ekleyin.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. Bölümünde, `Buttons` varolan düğme girişlerinden sonra, yeni belirtilen komutu temsil eden bir düğüm ekleyin.

    ```xml
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

    `DynamicItemStart`Bayrak, komutun dinamik olarak oluşturulmasını sağlar.

5. Yeni komutun görüntülenmesini test etmek için projeyi derleyin ve hata ayıklamayı başlatın.

    Yeni komut, **MRU yer tutucusunu** göstermek Için **TestMenu** menüsünde Yeni alt menüye, **alt menüye** tıklayın. Bir sonraki yordamda bir dinamik MRU komut listesi uygulandıktan sonra, bu komut etiketi, alt menü her açıldığında bu liste ile yerine geçer.

## <a name="filling-the-mru-list"></a>MRU listesini doldurma

1. *Testcommandpackageguid 'ler. cs* dosyasında, sınıf tanımındaki mevcut komut kimliklerinden sonra aşağıdaki satırları ekleyin `TestCommandPackageGuids` .

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. *TestCommand. cs* dosyasında aşağıdaki using ifadesini ekleyin.

    ```csharp
    using System.Collections;
    ```

3. Son AddCommand çağrısından sonra TestCommand yapıcısına aşağıdaki kodu ekleyin. `InitMRUMenu`Daha sonra tanımlanacaktır

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Aşağıdaki kodu TestCommand sınıfına ekleyin. Bu kod, MRU listesinde gösterilecek öğeleri temsil eden dizelerin listesini başlatır.

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

5. Yönteminden sonra `InitializeMRUList` `InitMRUMenu` yöntemini ekleyin. Bu, MRU liste menü komutlarını başlatır.

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

    MRU listesindeki olası her öğe için bir menü komut nesnesi oluşturmanız gerekir. IDE, `OnMRUQueryStatus` daha fazla öğe kalmayana kadar MRU listesindeki her öğe için yöntemini çağırır. Yönetilen kodda, IDE 'nin daha fazla öğe olmadığını öğrenmesi için tek yolu, önce tüm olası öğeleri oluşturmaktır. İsterseniz, `mc.Visible = false;` menü komutu oluşturulduktan sonra öğesini kullanarak ek öğeleri önce görünmez olarak işaretleyebilirsiniz. Bu öğeler daha sonra yönteminde kullanılarak görünür hale getirilebilir `mc.Visible = true;` `OnMRUQueryStatus` .

6. Yönteminden sonra `InitMRUMenu` aşağıdaki `OnMRUQueryStatus` yöntemi ekleyin. Bu, her MRU öğesi için metin ayarlayan işleyicidir.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Yönteminden sonra `OnMRUQueryStatus` aşağıdaki `OnMRUExec` yöntemi ekleyin. Bu, bir MRU öğesi seçmeye yönelik işleyicidir. Bu yöntem Seçili öğeyi listenin en üstüne taşıdıkça seçili öğeyi bir ileti kutusunda görüntüler.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
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

1. Projeyi derleyin ve hata ayıklamayı başlatın.

2. **TestMenu** menüsünde **TestCommand çağır**' a tıklayın. Bunu yaptığınızda komutun seçili olduğunu gösteren bir ileti kutusu görüntülenir.

    > [!NOTE]
    > Bu adım, VSPackage 'ın yüklenmesini zorlamak için gereklidir ve MRU listesini doğru şekilde görüntüler. Bu adımı atlarsanız, MRU listesi görüntülenmez.

3. **Test menüsü** menüsünde, **alt menü**' ye tıklayın. Dört öğe listesi, alt menünün sonunda bir ayırıcı altında görüntülenir. **Öğe 3**' e tıkladığınızda bir ileti kutusu görünmelidir ve metin, **Seçili öğe 3**' ü görüntüler. (Dört öğe listesi görüntülenmiyorsa, önceki adımda yer alan yönergeleri izlediğinizden emin olun.)

4. Alt menüyü yeniden açın. **Öğe 3** ' ün artık listenin başında ve diğer öğelerin bir konuma itildiğine dikkat edin. **Öğe 3** ' e yeniden tıklayın ve Ileti kutusunun **Seçili öğe 3**' ü görüntülediğine dikkat edin. Bu, metnin, komut etiketiyle birlikte yeni konuma doğru şekilde taşındığını gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Menü öğelerini dinamik olarak ekleme](../extensibility/dynamically-adding-menu-items.md)
