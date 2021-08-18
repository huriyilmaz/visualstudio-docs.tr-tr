---
title: Ayarlar Store | Microsoft Docs
description: Tüm kullanılabilir hizmetleri bulmak veya belirli bir hizmetin yüklü olup olmadığını belirlemek için ayarlar depolarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 668dce1e6cec7c27c3f816cfeb2131231983f571
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087190"
---
# <a name="get-service-information-from-the-settings-store"></a>Ayarlar mağazasından hizmet bilgilerini al
Tüm kullanılabilir hizmetleri bulmak veya belirli bir hizmetin yüklü olup olmadığını belirlemek için ayarlar depolarını kullanabilirsiniz. Hizmet sınıfının türünü biliyor olması gerekir.

## <a name="to-list-the-available-services"></a>Kullanılabilir hizmetleri listele

1. adlı bir VSIX projesi oluşturun `FindServicesExtension` ve ardından adlı özel bir komut `FindServicesCommand` ekleyin. Özel komut oluşturma hakkında daha fazla bilgi için [bkz. Menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

2. *FindServicesCommand.cs* içinde aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Yapılandırma ayarları deposuna gidin, ardından Hizmetler adlı alt aleyi bulun. Bu koleksiyon tüm kullanılabilir hizmetleri içerir. `MenuItemCommand`yönteminde, mevcut kodu kaldırın ve aşağıdakiyle değiştirin:

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

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

5. Deneysel örnekte, Araçlar  menüsünde **FindServices ÇağırKomand'a tıklayın.**

     Tüm hizmetleri listeleen bir ileti kutusu görüyorsanız.

     Bu ayarları doğrulamak için kayıt defteri düzenleyicisini kullanabilirsiniz.

## <a name="find-a-specific-service"></a>Belirli bir hizmeti bulma
 Belirli bir hizmetin yüklü <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> olup olmadığını belirlemek için yöntemini de kullanabilirsiniz. Hizmet sınıfının türünü biliyor olması gerekir.

1. Önceki yordamda oluşturduğunuz projenin MenuItemCallback içinde, hizmetin GUID'si tarafından adlandırılmış alt koleksiyonun yapılandırma ayarları deposu için arama `Services` yapın. Bu durumda Yardım hizmetine bakacağız.

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

2. Projeyi derleme ve hata ayıklamayı başlatma.

3. Deneysel örnekte, Araçlar  menüsünde **FindServices ÇağırKomand'a tıklayın.**

     Yardım Hizmeti Kullanılabilir: ve ardından True veya False **metninin** yer alan **bir ileti** **görüyorsanız.** Bu ayarı doğrulamak için, önceki adımlarda gösterildiği gibi bir kayıt defteri düzenleyicisi kullanabilirsiniz.
