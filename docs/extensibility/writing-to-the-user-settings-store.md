---
title: Kullanıcı ayarları deposuna yazma | Microsoft Docs
description: Bu kılavuzu kullanarak, Kullanıcı ayarları deposundan okuma ve yazma yoluyla Visual Studio 'ya bir dış araç olarak not defteri ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff3fa6f061f894abce17d2e6c58bfb791740a90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061777"
---
# <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma
Kullanıcı ayarları, **Araçlar/Seçenekler** iletişim kutusu, Özellikler pencereleri ve diğer diğer iletişim kutuları gibi yazılabilir ayarlardır. Visual Studio uzantıları, küçük miktarlarda veri depolamak için bunları kullanabilir. Bu izlenecek yol, Kullanıcı ayarları deposundan okuma ve yazma yoluyla Visual Studio 'ya bir dış araç olarak not defteri eklemeyi gösterir.

## <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma

1. UserSettingsStoreExtension adlı bir VSıX projesi oluşturun ve ardından UserSettingsStoreCommand adlı bir özel komut ekleyin. Özel bir komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

2. UserSettingsStoreCommand. cs dosyasında, aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. MenuItemCallback içinde, yönteminin gövdesini silin ve Kullanıcı ayarları deposunu aşağıdaki gibi alın:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Şimdi Not defteri 'nin zaten dış bir araç olarak ayarlanmış olup olmadığını öğrenin. ToolCmd ayarının "Notepad" olup olmadığını ve aşağıdaki gibi tüm dış araçları kullanarak yineleme yapmanız gerekir:

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

5. Not defteri bir dış araç olarak ayarlanmamışsa, aşağıdaki gibi ayarlayın:

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

6. Kodu test edin. Not defteri 'nin bir dış araç olarak eklediğini unutmayın, bu yüzden kayıt defterini ikinci bir kez çalıştırmadan önce geri almanız gerekir.

7. Kodu derleyin ve hata ayıklamayı başlatın.

8. **Araçlar** menüsünde **UserSettingsStoreCommand komutunu çağır**' a tıklayın. Bu, Not defteri 'Ni **Araçlar** menüsüne ekler.

9. Artık Araçlar/Seçenekler menüsünde Not defteri ' ni görmeniz ve **Not** defteri ' ne tıklamak, Not defteri 'nin bir örneğini göstermelidir.
