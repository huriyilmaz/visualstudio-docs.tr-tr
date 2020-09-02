---
title: Ayarlar deposundan hizmet bilgileri alınıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204305"
---
# <a name="getting-service-information-from-the-settings-store"></a>Ayarlar Deposu'ndan Hizmet Bilgilerini Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm kullanılabilir hizmetleri bulmak veya belirli bir hizmetin yüklenip yüklenmediğini öğrenmek için ayarlar deposunu kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.  
  
### <a name="to-list-the-available-services"></a>Kullanılabilir hizmetleri listelemek için  
  
1. Findservicesexten, adlı bir VSıX projesi oluşturun ve sonra FindServicesCommand adlı bir özel komut ekleyin. Özel bir komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. FindServicesCommand.cs ' de, aşağıdaki using deyimlerini ekleyin:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Yapılandırma ayarları deposunu alın ve ardından hizmet adlı alt koleksiyonu bulun. Bu koleksiyon, kullanılabilir tüm hizmetleri içerir. Menuıtemcommand yönteminde, var olan kodu kaldırın ve aşağıdaki kodla değiştirin:  
  
    ```  
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
  
4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.  
  
5. Deneysel örnekte, **Araçlar** menüsünde **Findservicescommand komutunu çağır**' a tıklayın.  
  
     Tüm hizmetlerin listelendiği bir ileti kutusu görmeniz gerekir.  
  
     Bu ayarları doğrulamak için kayıt defteri düzenleyicisini kullanabilirsiniz.  
  
## <a name="finding-a-specific-service"></a>Belirli bir hizmeti bulma  
 Ayrıca, <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> belirli bir hizmetin yüklenip yüklenmediğini anlamak için yöntemini de kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.  
  
1. Önceki yordamda oluşturduğunuz projenin MenuItemCallback öğesinde, `Services` hizmet GUID 'si tarafından adlandırılan alt koleksiyonun bulunduğu koleksiyon için yapılandırma ayarları deposunda arama yapın. Bu durumda, yardım hizmetine bakacağız.  
  
    ```  
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
  
2. Projeyi derleyin ve hata ayıklamayı başlatın.  
  
3. Deneysel örnekte, **Araçlar** menüsünde **Findservicescommand komutunu çağır**' a tıklayın.  
  
     Metin **yardım hizmeti kullanılabilir**  bir ileti görmeniz gerekir: **true** veya **false**. Bu ayarı doğrulamak için, önceki adımlarda gösterildiği gibi bir kayıt defteri düzenleyici kullanabilirsiniz.
