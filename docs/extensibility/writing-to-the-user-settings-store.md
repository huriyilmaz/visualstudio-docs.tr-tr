---
title: kullanıcı Ayarlar deposuna yazma | Microsoft Docs
description: bu kılavuzu kullanarak kullanıcı ayarları deposundan okuma ve yazma yoluyla Visual Studio bir dış araç olarak Not Defteri eklemeyi öğrenin.
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
ms.openlocfilehash: cb169700ea55eb8bd4d1a762fa5e8d082c04981df1573255d18ca8d41bb3955a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334932"
---
# <a name="writing-to-the-user-settings-store"></a>Kullanıcı Ayarları Deposuna Yazma
Kullanıcı ayarları, **Araçlar/Seçenekler** iletişim kutusu, Özellikler pencereleri ve diğer diğer iletişim kutuları gibi yazılabilir ayarlardır. Visual Studio uzantılar, bunları küçük miktarlarda veri depolamak için kullanabilir. bu izlenecek yol, kullanıcı ayarları deposundan okuma ve yazma yoluyla Visual Studio bir dış araç olarak Not Defteri nasıl ekleneceğini gösterir.

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

4. şimdi Not Defteri zaten dış bir araç olarak ayarlanmış olup olmadığını öğrenin. toolcmd ayarının "Not Defteri" olup olmadığını ve aşağıdaki gibi tüm dış araçları kullanarak yineleme yapmanız gerekir:

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

5. Not Defteri dış bir araç olarak ayarlanmamışsa, aşağıdaki gibi ayarlayın:

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

6. Kodu test edin. Not Defteri dış bir araç olarak eklediğini unutmayın. bu nedenle, ikinci kez çalıştırmadan önce kayıt defterini geri almanız gerekir.

7. Kodu derleyin ve hata ayıklamayı başlatın.

8. **Araçlar** menüsünde **UserSettingsStoreCommand komutunu çağır**' a tıklayın. bu işlem, **araçlar** menüsüne Not Defteri ekler.

9. artık araçlar/seçenekler menüsünde Not Defteri görmeniz gerekir ve **Not Defteri** ' a tıklayarak Not Defteri örneğini almalıdır.
