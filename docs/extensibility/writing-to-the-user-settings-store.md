---
title: User Ayarlar Store | Microsoft Docs
description: Bu kılavuzda, Not Defteri Visual Studio okuma ve yazma adımlarını kullanarak dış araç olarak kullanıcı ayarları deposuna veri ekleme hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b27796000919336e2585d5b3e7c288a88abe261f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724942"
---
# <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma
Kullanıcı ayarları Araçlar **/** Seçenekler iletişim kutusundakiler, özellikler pencereleri ve bazı diğer iletişim kutuları gibi yazılabilir ayarlardır. Visual Studio uzantıları bunları küçük miktarlarda veri depolamak için kullanabilir. Bu kılavuzda, kullanıcı ayarları Not Defteri yazarak Visual Studio aracı olarak bir dış araç olarak depolamaya veri ekleme hakkında bilgi edinebilirsiniz.

## <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma

1. UserSettingsStoreExtension adlı bir VSIX projesi oluşturun ve ardından UserSettingsStoreCommand adlı özel bir komut ekleyin. Özel komut oluşturma hakkında daha fazla bilgi için bkz. [Menü Komutuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

2. UserSettingsStoreCommand.cs içinde aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. MenuItemCallback'te yönteminin gövdelerini silin ve kullanıcı ayarları depolarını aşağıdaki gibi edinin:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Şimdi, Not Defteri bir dış araç olarak ayarlanmış olup olmadığını bulun. ToolCmd ayarının "varsayılan" olup olmadığını belirlemek için tüm dış araçlarda Not Defteri gerekir:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Dış Not Defteri bir araç olarak ayarlanmamışsa, bunu aşağıdaki gibi ayarlayın:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Kodu test etmek. Bir Dış Araç Not Defteri ekli olduğunu unutmayın, bu nedenle kayıt defterini ikinci kez çalıştırmadan önce geri alasiniz.

7. Kodu derleme ve hata ayıklamayı başlatma.

8. Araçlar menüsünde **UserSettingsStoreCommand'i Çağır'a tıklayın.**  Bu, Not Defteri menüye yeni **bir ekleme** ekler.

9. Şimdi Araçlar / Not Defteri menüsünde bu seçeneği görüyor ve Not Defteri'e **tıklayarak** Not Defteri.
