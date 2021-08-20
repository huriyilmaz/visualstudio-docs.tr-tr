---
title: 'İzlenecek yol: başlangıç sayfasına özel XAML ekleme | Microsoft Docs'
description: bu yönergeyi kullanarak web tarayıcısı içeren özel bir Visual Studio başlangıç sayfası oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4da513c5040b6da97a9a545b5b40892d8cdc4c30
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158053"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>İzlenecek yol: başlangıç sayfasına özel XAML ekleme

bu izlenecek yol, bir Web tarayıcısı içeren özel bir Visual Studio başlangıç sayfası oluşturmayı gösterir.

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

1. **F5** tuşuna basın.

     Visual Studio deneysel örneği, özel başlangıç sayfası yüklüyken, ancak seçilmediğinden açılır.

2. Visual Studio deneysel örneğinde **araçlar/seçenekler/ortam** sayfasını açın.

3. **Başlatma**' yı seçin. **Başlangıç sayfası Özelleştir** listesinde, *. xaml* dosyanızı seçin ve **Tamam**' a tıklayın.

4. **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.

5. **Bing** sekmesine tıklayın.

     bir Bing web sayfası görmeniz gerekir.

6. **MyButton** sekmesine tıklayın.

     **yeni Project** iletişim kutusunu açan bir **myproject** düğmesi görmeniz gerekir.

7. Deneysel örneği kapatın.

Özel başlangıç sayfasını uygulamak için, **Araçlar**  >  **Seçenekler**  >  **ortamında**, **Başlangıç**' ı seçin. **Başlangıç sayfası Özelleştir** listesinde, *. xaml* dosyanızı seçin ve **Tamam**' a tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio başlangıç sayfası şimdi bir Web tarayıcısı sekmesi ve MyButton sekmesini görüntüleyen bir sekme içerir. [Başlangıç sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)bölümünde gösterildiği gibi özel bir .dll eklemek için  başka işlevlere sahip özel başlangıç sayfaları oluşturabilirsiniz. elde edilen. vsix dosyasını [Visual Studio market](https://marketplace.visualstudio.com/) Web sitesinde veya başka bir web sitesi veya ağ paylaşımında yayımlayarak özel başlangıç sayfalarını diğer kullanıcılarla paylaşabilirsiniz. Daha fazla bilgi için bkz. [özel başlangıç sayfaları dağıtma](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF kapsayıcı denetimleri](/previous-versions/bb675291(v=vs.110))