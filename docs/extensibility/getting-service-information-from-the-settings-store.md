---
title: Ayarlar Mağazasından Servis Bilgileri Alma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711368"
---
# <a name="get-service-information-from-the-settings-store"></a>Ayarlar mağazasından servis bilgilerini alma
Ayarlar mağazasını kullanılabilir tüm hizmetleri bulmak veya belirli bir hizmetin yüklü olup olmadığını belirlemek için kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.

## <a name="to-list-the-available-services"></a>Kullanılabilir hizmetleri listelemek için

1. Adlı `FindServicesExtension` bir VSIX projesi oluşturun ve `FindServicesCommand`ardından özel bir komut ekleyin. Özel komut oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. *FindServicesCommand.cs,* aşağıdaki yönergeleri kullanarak ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Yapılandırma ayarları deposunu edinin ve ardından Hizmetler adlı alt koleksiyonu bulun. Bu koleksiyon, kullanılabilir tüm hizmetleri içerir. `MenuItemCommand` Yöntemde, varolan kodu kaldırın ve aşağıdakilerle değiştirin:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

5. Deneme örneğinde, **Araçlar** menüsünde, **FindServicesCommand'ı çağır'ı**tıklatın.

     Tüm hizmetleri listeleyen bir ileti kutusu görmeniz gerekir.

     Bu ayarları doğrulamak için kayıt defteri düzenleyicisini kullanabilirsiniz.

## <a name="find-a-specific-service"></a>Belirli bir hizmeti bulma
 Belirli bir hizmetin <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> yüklü olup olmadığını belirlemek için yöntemi de kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.

1. Önceki yordamda oluşturduğunuz projenin MenuItemCallback'inde, hizmetin GUID `Services` tarafından adlandırılmış alt koleksiyonuna sahip koleksiyon için yapılandırma ayarları deposunda arama yapın. Bu durumda Yardım hizmetini arayacağız.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Projeyi oluşturun ve hata ayıklamaya başlayın.

3. Deneme örneğinde, **Araçlar** menüsünde, **FindServicesCommand'ı çağır'ı**tıklatın.

     Kullanılabilir metin Yardım Hizmeti ile bir ileti görmeniz **gerekir:** **Doğru** veya **Yanlış**takip. Bu ayarı doğrulamak için, önceki adımlarda gösterildiği gibi bir kayıt defteri düzenleyicisi kullanabilirsiniz.
