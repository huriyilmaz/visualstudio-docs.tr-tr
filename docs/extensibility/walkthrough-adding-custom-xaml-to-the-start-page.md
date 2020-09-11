---
title: 'İzlenecek yol: başlangıç sayfasına özel XAML ekleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 85cc6520ea86db664de676232e8d61a643483ca4
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012080"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>İzlenecek yol: başlangıç sayfasına özel XAML ekleme

Bu izlenecek yol, bir Web tarayıcısı içeren özel bir Visual Studio başlangıç sayfası oluşturmayı gösterir.

## <a name="add-custom-xaml"></a>Özel XAML Ekle

1. [Özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md)bölümündeki yönergeleri izleyerek bir başlangıç sayfası oluşturun.

2. *MainWindow. xaml* dosyasında \<Grid> bölümünü bulun.

3. \<TabControl> \<TabItem> \< Grid> Aşağıdaki örnekte gösterildiği gibi bir öğesi ve öğesi içine ekleyin.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. \<TabItem>Yeni bir proje açan bir öğe ile ikinci bir ekleyin \<Button> :

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Özel başlangıç sayfasını test etme

1. **F5**tuşuna basın.

     Visual Studio 'nun deneysel örneği, özel başlangıç sayfası yüklenmiş ancak seçilmemiş olarak açılır.

2. Visual Studio 'nun deneysel örneğinde **Araçlar/Seçenekler/ortam** sayfasını açın.

3. **Başlatma**' yı seçin. **Başlangıç sayfası Özelleştir** listesinde, *. xaml* dosyanızı seçin ve **Tamam**' a tıklayın.

4. **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.

5. **Bing** sekmesine tıklayın.

     Bing Web sayfası görmeniz gerekir.

6. **MyButton** sekmesine tıklayın.

     **Yeni proje** iletişim kutusunu açan bir **MyProject** düğmesi görmeniz gerekir.

7. Deneysel örneği kapatın.

Özel başlangıç sayfasını uygulamak için, **Araçlar**  >  **Seçenekler**  >  **ortamında**, **Başlangıç**' ı seçin. **Başlangıç sayfası Özelleştir** listesinde, *. xaml* dosyanızı seçin ve **Tamam**' a tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio başlangıç sayfasında artık bir Web tarayıcısı sekmesi ve MyButton sekmesi görüntülenen bir sekme bulunur. [Başlangıç sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)bölümünde gösterildiği *gibi, özel* bir. dll eklemek için başka işlevlere sahip özel başlangıç sayfaları oluşturabilirsiniz. Elde edilen. vsix dosyasını [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine veya başka bir Web sitesi ya da ağ paylaşımında yayımlayarak, özel başlangıç sayfalarını diğer kullanıcılarla paylaşabilirsiniz. Daha fazla bilgi için bkz. [özel başlangıç sayfaları dağıtma](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF kapsayıcı denetimleri](/previous-versions/bb675291(v=vs.110))