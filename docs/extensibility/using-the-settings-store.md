---
title: Ayarlar deposunu kullanma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9c42835e720fd3c33e53d862192e3e2863a4423
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632592"
---
# <a name="using-the-settings-store"></a>Ayarlar Deposu Kullanma
İki tür ayar deposu vardır:

- Salt okunurdur, Visual Studio ve VSPackage ayarları olan yapılandırma ayarları. Visual Studio, bilinen tüm. pkgdef dosyalarındaki ayarları bu depoya birleştirir.

- **Seçenekler** iletişim kutusunda, özellik sayfalarında ve bazı diğer iletişim kutularında görüntülenenler gibi yazılabilir ayarlar olan Kullanıcı ayarları. Visual Studio uzantıları bunları, küçük miktarlarda verilerin yerel depolaması için kullanabilir.

  Bu izlenecek yol, yapılandırma ayarı deposundan verilerin nasıl okunacağını gösterir. Kullanıcı ayarları deposuna yazma hakkında bir açıklama için bkz. [Kullanıcı ayarları deposuna yazma](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Örnek proje oluşturma
 Bu bölümde, gösterim için bir menü komutuyla basit uzantı projesi oluşturma gösterilmektedir.

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. @No__t_1 adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSıX projesi oluşturun. VSıX proje şablonunu **görsel C# /genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Şimdi **SettingsStoreCommand**adlı özel bir komut öğesi şablonu ekleyin. **Yeni öğe Ekle** iletişim kutusunda,  **C# görsel/genişletilebilirlik** ' e gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını **SettingsStoreCommand.cs**olarak değiştirin. Özel bir komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Yapılandırma ayarları deposunu kullanma
 Bu bölümde yapılandırma ayarlarını algılama ve görüntüleme işlemlerinin nasıl yapılacağı gösterilmektedir.

1. SettingsStorageCommand.cs dosyasında aşağıdaki yönergeleri kullanarak aşağıdakileri ekleyin:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. @No__t_0, yönteminin gövdesini kaldırın ve bu satırları ekleyerek yapılandırma ayarları deposunu alın:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    @No__t_0, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> hizmeti üzerinde yönetilen bir yardımcı sınıftır.

3. Şimdi Windows Phone araçlarının yüklenip yüklenmediğini öğrenin. Kod şöyle görünmelidir:

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

    **Microsoft Windows Phone Geliştirici Araçları** belirten bir ileti kutusu görmeniz gerekir: ardından **true** veya **false**.

   Visual Studio, sistem kayıt defterinde ayarlar deposunu saklar.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Yapılandırma ayarlarını doğrulamak üzere bir kayıt defteri Düzenleyicisi kullanmak için

1. Regedit. exe dosyasını açın.

2. HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts \\ gidin.

    > [!NOTE]
    > \14.0Exp_Config\ öğesini içeren anahtara baktığınızdan emin olun \\. Visual Studio 'nun Deneysel örneğini çalıştırdığınızda yapılandırma ayarları "14.0 Exp_Config" kayıt defteri kovanında bulunur.

3. \Yüklü Ürünler \ düğümünü genişletin. Önceki adımlarda bulunan ileti **microsoft Windows Phone Geliştirici Araçları yüklüyse: true**ise, \Yüklü Ürünler \ bir Microsoft Windows Phone Geliştirici Araçları düğümü içermelidir. İleti **microsoft Windows Phone Geliştirici Araçları yüklüyse: false**ise, \Yüklü Ürünler \ microsoft Windows Phone Geliştirici Araçları düğümü içermemelidir.
