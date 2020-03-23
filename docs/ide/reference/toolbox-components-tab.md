---
title: Araç Kutusu, Bileşenler Sekmesi
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5eb8c320a3190121d95395f7b359aa9ed978408
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597314"
---
# <a name="toolbox-components-tab"></a>Araç Kutusu, Bileşenler sekmesi

Windows Formlar için Visual Basic ve C# tasarımcılarına ekleyebileceğiniz bileşenleri görüntüler. Visual Studio ile birlikte verilen ve <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> bileşenler gibi .NET bileşenlerine ek olarak, bu sekmeye kendi veya üçüncü taraf bileşenlerinizi ekleyebilirsiniz.

Bu sekmeyi görüntülemek için bir Windows Forms tasarımcısı açın. **Araç Kutusunu** **Görüntüle'yi** > seçin. **Araç Kutusu'nda** **Bileşenler** sekmesini seçin.

## <a name="components"></a>Bileşenler

**Backgroundworker**

Ayrı, <xref:System.ComponentModel.BackgroundWorker> özel bir iş parçacığı üzerinde bir işlem çalıştırabilirsiniz bir bileşen örneği oluşturur. Daha fazla bilgi için [BackgroundWorker bileşenine](/dotnet/framework/winforms/controls/backgroundworker-component)bakın.

**Directoryentry**

Etkin Dizin hiyerarşisinde bir düğümü veya nesneyi kapsülleyen ve Etkin Dizin hizmet sağlayıcılarıyla etkileşimde kullanılmak üzere kullanılabilen bir <xref:System.DirectoryServices.DirectoryEntry> bileşen örneği oluşturur.

**DizinArama**

Etkin Dizin'e karşı sorguları gerçekleştirmek için kullanabileceğiniz bir <xref:System.DirectoryServices.DirectorySearcher> bileşen örneği oluşturur.

**Hata Sağlayıcısı**

Bir <xref:System.Windows.Forms.ErrorProvider> form üzerindeki denetimin onunla ilişkili bir hatası olduğunu son kullanıcıya gösteren bir bileşen örneği oluşturur. Daha fazla bilgi için [Hata Sağlayıcısı bileşenine](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)bakın.

**Eventlog**

Olayları bir <xref:System.Diagnostics.EventLog> günlük günlüğüne yazma ve günlük verilerini okuma dahil olmak üzere sistem ve özel olay günlükleriyle etkileşimde kalmak için kullanabileceğiniz bir bileşen örneği oluşturur.

**Filesystemwatcher**

Erişebildiğiniz <xref:System.IO.FileSystemWatcher> herhangi bir dizin veya dosyadaki değişiklikleri izlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**Yardım Sağlayıcısı**

Denetimler <xref:System.Windows.Forms.HelpProvider> için açılır pencere veya çevrimiçi yardım sağlayan bir bileşen örneği oluşturur. Daha fazla bilgi için [HelpProvider bileşenine](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms)bakın.

**ımagelist**

Nesne koleksiyonunu <xref:System.Windows.Forms.ImageList> yönetmek için yöntemler sağlayan bir bileşen örneği oluşturur. <xref:System.Drawing.Image> Daha fazla bilgi için [ImageList bileşenine](/dotnet/framework/winforms/controls/imagelist-component-windows-forms)bakın.

**Messagequeue**

İleti kuyruklarıyla etkileşimde kalmak için kullanabileceğiniz, iletileri okuma ve kuyruklara ileti yazma, hareketleri işleme ve sıra yönetimi görevlerini gerçekleştirme gibi kullanabileceğiniz bir <xref:System.Messaging.MessageQueue> bileşen örneği oluşturur.

**Performancecounter**

Yeni kategoriler <xref:System.Diagnostics.PerformanceCounter> ve örnekler oluşturma, sayaçlardan değerleri okuma ve sayaç verileri üzerinde hesaplamalar gerçekleştirme gibi Windows performans sayaçlarıyla etkileşimde kullanılmak üzere kullanabileceğiniz bir bileşen örneği oluşturur.

**İşleme**

Sisteminizdeki <xref:System.Diagnostics.Process> işlemlerle ilişkili verileri durdurmak, başlatmak ve işlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**Serialport**

Senkron <xref:System.IO.Ports.SerialPort> ve olay odaklı G/Ç sağlayan bir bileşen örneği, pin ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlar.

**Servicecontroller**

Hizmetleri başlatma <xref:System.ServiceProcess.ServiceController> ve durdurma ve onlara komut gönderme dahil olmak üzere varolan hizmetleri işlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**Zamanlayıcı**

Windows tabanlı <xref:System.Windows.Forms.Timer> uygulamalarınıza zaman tabanlı işlevsellik eklemek için kullanabileceğiniz bir bileşen örneği oluşturur. Daha fazla bilgi için [Timer bileşenine](/dotnet/framework/winforms/controls/timer-component-windows-forms)bakın.

> [!NOTE]
> <xref:System.Timers.Timer> **Ayrıca, Araç Kutusuna** ekleyebileceğiniz bir sistem <xref:System.Timers.Timer> tabanlı dır Bu sunucu uygulamaları için <xref:System.Windows.Forms.Timer> optimize edive Windows Formları Windows Formlar'da kullanım için en uygun uyrabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Formlarında kullanılacak denetimler](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Toolbox öğelerini, WPF bileşenlerini seçin](choose-toolbox-items-wpf-components.md)
- [Araç Kutusu](../../ide/reference/toolbox.md)
