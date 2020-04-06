---
title: Kullanıcı Ayarları Mağazasına Yazma | Microsoft Dokümanlar
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740368"
---
# <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma
Kullanıcı **ayarları, Araçlar / Seçenekler** iletişim kutusundakiler, özellikler pencereleri ve diğer bazı iletişim kutularındaki ler gibi yazılabilir ayarlardır. Visual Studio uzantıları bunları az miktarda veri depolamak için kullanabilir. Bu walkthrough, kullanıcı ayarları mağazasından okuyarak ve yazarak Visual Studio'ya harici bir araç olarak Not Defteri'nin nasıl ekleyeceğinigösterir.

## <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma

1. UserSettingsStoreExtension adında bir VSIX projesi oluşturun ve ardından UserSettingsStoreCommand adında özel bir komut ekleyin. Özel komut oluşturma hakkında daha fazla bilgi için [Menü Komutu yla Uzantı Oluşturma'ya](../extensibility/creating-an-extension-with-a-menu-command.md) bakın

2. UserSettingsStoreCommand.cs, aşağıdaki yönergeleri kullanarak ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. MenuItemCallback'de yöntemin gövdesini silin ve aşağıdaki gibi kullanıcı ayarları deposuna girin:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Şimdi Notepad'in harici bir araç olarak ayarlanıp ayarlanmadığını öğrenin. ToolCmd ayarının aşağıdaki gibi "Not Defteri" olup olmadığını belirlemek için tüm dış araçları doğrulamanız gerekir:

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

5. Not Defteri harici bir araç olarak ayarlanmadıysa, aşağıdaki gibi ayarlayın:

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

6. Kodu test edin. Not Defteri'ni Harici Bir Araç olarak eklediği için ikinci kez çalıştırmadan önce kayıt defterini geri almanız gerektiğini unutmayın.

7. Kodu oluşturun ve hata ayıklamaya başlayın.

8. **Araçlar** menüsünde, **Invoke UserSettingsStoreCommand'ı**tıklatın. Bu, **Araçlar** menüsüne Not Defteri ekler.

9. Şimdi Araçlar / Seçenekler menüsünde Not Defteri görmeli ve **Not Defteri'ni** tıklatarak Not Defteri'nin bir örneğini gündeme getirmelisiniz.
