---
title: Araç Kutusu, Bileşenler Sekmesi
description: Araç Kutusu penceresinin Bileşenler sekmesinde bulunan bileşenler hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6925baa2d396d2b01839cdd9af083eb20867b191
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123768"
---
# <a name="toolbox-components-tab"></a>Araç Kutusu, Bileşenler sekmesi

Windows Forms için Visual Basic ve C# tasarımcılarına ek Windows görüntüler. ve bileşenleri gibi, Visual Studio.NET bileşenlerine ek olarak, kendi veya üçüncü taraf bileşenlerinizi de bu <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> sekmeye ebilirsiniz.

Bu sekmeyi görüntülemek için bir Windows Forms tasarımcısı açın. Görünüm **Araç**  >  **Kutusu'nı seçin.** Araç **Kutusu'da** Bileşenler **sekmesini** seçin.

## <a name="components"></a>Bileşenler

**Backgroundworker**

Ayrı, <xref:System.ComponentModel.BackgroundWorker> ayrılmış bir iş parçacığında işlem çalıştıracak bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [BackgroundWorker bileşeni.](/dotnet/framework/winforms/controls/backgroundworker-component)

**Directoryentry**

Active Directory hiyerarşisinde bir düğümü veya nesneyi kapsüller ve Active Directory hizmet sağlayıcılarıyla etkileşim kurmak için kullanılabilir bir <xref:System.DirectoryServices.DirectoryEntry> bileşen örneği oluşturur.

**DirectorySearcher**

Active <xref:System.DirectoryServices.DirectorySearcher> Directory'ye karşı sorgular gerçekleştirmek için kullanabileceğiniz bir bileşen örneği oluşturur.

**ErrorProvider**

Bir form üzerinde bir denetimin ilişkili bir hataya sahip olduğunu son <xref:System.Windows.Forms.ErrorProvider> kullanıcıya gösteren bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [ErrorProvider bileşeni.](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)

**Eventlog**

Sistem ve özel olay günlükleri ile etkileşim kurmak için kullanabileceğiniz bir bileşen örneği oluşturur; örneğin, olayları bir günlüğe yazma <xref:System.Diagnostics.EventLog> ve günlük verilerini okuma.

**Filesystemwatcher**

Erişiminiz <xref:System.IO.FileSystemWatcher> olan herhangi bir dizin veya dosyada yapılan değişiklikleri izlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**HelpProvider**

Denetimler <xref:System.Windows.Forms.HelpProvider> için açılır pencere veya çevrimiçi yardım sağlayan bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [HelpProvider bileşeni.](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms)

**ımagelist**

Bir <xref:System.Windows.Forms.ImageList> nesne koleksiyonunu yönetmek için yöntemler sağlayan bir bileşen örneği <xref:System.Drawing.Image> oluşturur. Daha fazla bilgi için bkz. [ImageList bileşeni.](/dotnet/framework/winforms/controls/imagelist-component-windows-forms)

**Messagequeue**

İletileri okuma ve kuyruklara ileti yazma, işlemleri işleme ve kuyruk yönetim görevlerini gerçekleştirme gibi ileti kuyruklarıyla etkileşim kurmak için kullanabileceğiniz <xref:System.Messaging.MessageQueue> bir bileşen örneği oluşturur.

**Performancecounter**

Yeni kategoriler ve örnekler oluşturma, Windows sayaçlardan değerleri okuma ve sayaç verilerinde hesaplamalar gerçekleştirme gibi performans sayaçlarıyla etkileşim kurmak için kullanabileceğiniz bir bileşen <xref:System.Diagnostics.PerformanceCounter> örneği oluşturur.

**İşleme**

Sisteminiz <xref:System.Diagnostics.Process> üzerinde işlemlerle ilişkili verileri durdurmak, başlatmak ve işlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**Serialport**

Zaman uyumlu <xref:System.IO.Ports.SerialPort> ve olay odaklı bir I/O, sabitleme ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlayan bir bileşen örneği oluşturur.

**Servicecontroller**

Hizmetleri başlatma ve durdurma ve onlara komut gönderme de dahil olmak üzere mevcut hizmetleri işlemek <xref:System.ServiceProcess.ServiceController> için kullanabileceğiniz bir bileşen örneği oluşturur.

**Zamanlayıcı**

Uygulama <xref:System.Windows.Forms.Timer> tabanlı uygulamalarınıza zaman tabanlı işlevsellik eklemek için kullanabileceğiniz bir Windows örneği oluşturur. Daha fazla bilgi için bkz. [Zamanlayıcı bileşeni.](/dotnet/framework/winforms/controls/timer-component-windows-forms)

> [!NOTE]
> Araç Kutusu'na ek olarak ek kullanabileceğiniz bir sistem tabanlı da vardır. Bu, sunucu uygulamaları için iyileştirilmiştir ve Windows Forms, Windows <xref:System.Timers.Timer>  <xref:System.Timers.Timer> <xref:System.Windows.Forms.Timer> Forms'ta kullanım için uygundur.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Windows denetimleri](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Araç Kutusu öğelerini, WPF bileşenlerini seçme](choose-toolbox-items-wpf-components.md)
- [Araç Kutusu](../../ide/reference/toolbox.md)
