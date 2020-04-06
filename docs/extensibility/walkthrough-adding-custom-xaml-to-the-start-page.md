---
title: 'Walkthrough: Başlangıç Sayfasına Özel XAML Ekleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697689"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Walkthrough: Başlangıç sayfasına özel XAML ekleme

Bu iz, Web tarayıcısı içeren özel bir Visual Studio başlangıç sayfasının nasıl oluşturulurolduğunu gösterir.

## <a name="add-custom-xaml"></a>Özel XAML ekle

1. Özel bir başlangıç sayfası oluştur'daki yönergeleri izleyerek [bir başlangıç sayfası oluşturun.](../extensibility/creating-a-custom-start-page.md)

2. *MainWindow.xaml* \<dosyasında, Grid> bölümünü bulun.

3. Aşağıdaki \<örnekte gösterildiği gibi, Bir Sekdenetimi> öğesi ve \< \< Grid> öğesi içinde bir TabItem> ekleyin.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Yeni bir \<proje yi açan \<düğme> öğesiyle ikinci bir TabItem> ekleyin:

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

## <a name="test-the-custom-start-page"></a>Özel başlangıç sayfasını test edin

1. **F5 tuşuna**basın.

     Visual Studio'nun deneysel örneği, özel başlangıç sayfası yüklü ancak seçilmemiş olarak açılır.

2. Visual Studio'nun deneysel örneğinde **Araçlar /Seçenekler / Çevre** sayfasını açın.

3. **Başlangıç'ı**seçin. Başlat **Sayfasını Özelleştir** listesinde *.xaml* dosyanızı seçin ve **Tamam'ı**tıklatın.

4. **Görünüm** menüsünde, **Başlat Sayfasını**tıklatın.

5. **Bing** sekmesini tıklatın.

     Bing web sayfasına bakmalısınız.

6. **MyButton** sekmesini tıklatın.

     **Yeni Proje** iletişim kutusunu açan bir **MyProject** düğmesini görmeniz gerekir.

7. Deneysel örneği kapatın.

**Araçlar** > **Seçenekleri** > **Ortamı'nda**özel başlangıç sayfasını uygulamak için **Başlangıç'ı**seçin. Başlat **Sayfasını Özelleştir** listesinde *.xaml* dosyanızı seçin ve **Tamam'ı**tıklatın.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio başlangıç sayfası artık bir Web tarayıcısı sekmesi ve MyButton sekmesigörüntüleyen bir sekme içerir. [Başlangıç Sayfasına Kullanıcı Denetimi Ekleme'de](../extensibility/adding-user-control-to-the-start-page.md)gösterildiği gibi, özel bir .dll eklemek için *kod arkası* modelini kullanarak başka işlevlere sahip özel başlangıç sayfaları oluşturabilirsiniz. Elde edilen .vsix dosyasını [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Web sitesine veya başka bir Web sitesine veya ağ paylaşımına yayınlayarak özel başlangıç sayfalarını diğer kullanıcılarla paylaşabilirsiniz. Daha fazla bilgi için bkz: [Özel Başlangıç Sayfalarını Dağıtma.](../extensibility/deploying-custom-start-pages.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF konteyner kontrolleri](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
