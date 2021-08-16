---
title: Ayarlar deposunu kullanma | Microsoft Docs
description: salt okunurdur Visual Studio ve vspackage ayarları olan yapılandırma ayarı deposundan verileri nasıl okuyacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5777959fe8ca21d3e560f935285ca8a0a3885a441a0118f6ade8a40b208a5bc7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375149"
---
# <a name="using-the-settings-store"></a>Ayarlar Deposu Kullanma
İki tür ayar deposu vardır:

- salt okunurdur Visual Studio ve vspackage ayarları olan yapılandırma ayarları. Visual Studio bilinen tüm. pkgdef dosyalarındaki ayarları bu depoya birleştirir.

- **Seçenekler** iletişim kutusunda, özellik sayfalarında ve bazı diğer iletişim kutularında görüntülenenler gibi yazılabilir ayarlar olan Kullanıcı ayarları. Visual Studio uzantılar bunları küçük miktarlarda verilerin yerel depolaması için kullanabilir.

  Bu izlenecek yol, yapılandırma ayarı deposundan verilerin nasıl okunacağını gösterir. kullanıcı ayarları deposuna yazma hakkında bir açıklama için bkz. [kullanıcı Ayarlar deposuna yazma](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Örnek Project oluşturma
 Bu bölümde, gösterim için bir menü komutuyla basit uzantı projesi oluşturma gösterilmektedir.

1. her Visual Studio uzantısı, uzantı varlıklarını içeren bir vsıx dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projesi oluşturun `SettingsStoreExtension` . vsıx proje şablonunu, **Visual C#/genişletilebilirlik** altındaki **yeni Project** iletişim kutusunda bulabilirsiniz.

2. Şimdi **SettingsStoreCommand** adlı özel bir komut öğesi şablonu ekleyin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını **SettingsStoreCommand. cs** olarak değiştirin. Özel bir komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>yapılandırma Ayarlar deposunu kullanma
 Bu bölümde yapılandırma ayarlarını algılama ve görüntüleme işlemlerinin nasıl yapılacağı gösterilmektedir.

1. SettingsStorageCommand. cs dosyasında aşağıdaki yönergeleri kullanarak aşağıdakileri ekleyin:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. İçinde `MenuItemCallback` , yönteminin gövdesini kaldırın ve bu satırları ekleyerek yapılandırma ayarları deposunu alın:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    , <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Hizmet üzerinde yönetilen bir yardımcı sınıftır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> .

3. şimdi Windows Phone araçlarının yüklenip yüklenmediğini öğrenin. Kod şöyle görünmelidir:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Kodu test edin. Projeyi derleyin ve hata ayıklamayı başlatın.

5. Deneysel örnekte, **Araçlar** menüsünde **SettingsStoreCommand komutunu çağır**' a tıklayın.

    **Microsoft Windows Phone Geliştirici Araçları** belirten bir ileti kutusu görmeniz gerekir: ardından **True** veya **False**.

   Visual Studio, sistem kayıt defterinde ayarları saklar.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Yapılandırma ayarlarını doğrulamak üzere bir kayıt defteri Düzenleyicisi kullanmak için

1. Regedit.exe açın.

2. HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProductsgidin \\ .

    > [!NOTE]
    > \ 14.0Exp_Config \ içeren ve \ 14.0_Config olmayan anahtara baktığınızdan emin olun \\ . Visual Studio deneysel örneğini çalıştırdığınızda yapılandırma ayarları "14.0Exp_Config" kayıt defteri kovanında bulunur.

3. \Yüklü Ürünler \ düğümünü genişletin. önceki adımlarda bulunan ileti **microsoft Windows Phone Geliştirici Araçları yüklüyse: True** ise, \yüklü ürünler \ bir Microsoft Windows Phone Geliştirici Araçları düğümü içermelidir. ileti **microsoft Windows Phone Geliştirici Araçları yüklüyse: False** ise, \yüklü ürünler \ microsoft Windows Phone Geliştirici Araçları düğümü içermemelidir.
