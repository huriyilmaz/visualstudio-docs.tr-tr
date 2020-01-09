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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597314"
---
# <a name="toolbox-components-tab"></a>Araç kutusu, bileşenler sekmesi

Windows Forms için Visual Basic ve C# tasarımcılara ekleyebileceğiniz bileşenleri görüntüler. <xref:System.Messaging.MessageQueue> ve <xref:System.Diagnostics.EventLog> bileşenleri gibi Visual Studio 'da bulunan .NET bileşenlerine ek olarak, kendi veya üçüncü taraf bileşenlerinizi bu sekmeye ekleyebilirsiniz.

Bu sekmeyi göstermek için bir Windows Forms Tasarımcısı açın.  > **araç kutusunu** **görüntüle** ' yi seçin. **Araç kutusu**' nda **Bileşenler** sekmesini seçin.

## <a name="components"></a>Bileşenler

**BackgroundWorker**

Ayrı ve adanmış bir iş parçacığında bir işlemi çalıştırabilede bir <xref:System.ComponentModel.BackgroundWorker> bileşen örneği oluşturur. Daha fazla bilgi için bkz. [BackgroundWorker Component](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Active Directory hiyerarşisinde bir düğüm veya nesneyi kapsülleyen ve Active Directory servis sağlayıcılarıyla etkileşim kurmak için kullanılabilen bir <xref:System.DirectoryServices.DirectoryEntry> bileşen örneği oluşturur.

**DirectorySearcher**

Active Directory karşı sorguları gerçekleştirmek için kullanabileceğiniz bir <xref:System.DirectoryServices.DirectorySearcher> bileşen örneği oluşturur.

**ErrorProvider**

Son kullanıcıya, formdaki bir denetimin bir hata ile ilişkili bir hata olduğunu gösteren <xref:System.Windows.Forms.ErrorProvider> bileşen örneği oluşturur. Daha fazla bilgi için bkz. [ErrorProvider Component](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Bir günlüğe olay yazmak ve günlük verilerini okumak dahil olmak üzere sistem ve özel olay günlükleriyle etkileşim kurmak için kullanabileceğiniz bir <xref:System.Diagnostics.EventLog> bileşen örneği oluşturur.

**FileSystemWatcher**

Erişiminiz olan herhangi bir dizin veya dosyadaki değişiklikleri izlemek için kullanabileceğiniz bir <xref:System.IO.FileSystemWatcher> bileşen örneği oluşturur.

**HelpProvider**

Denetimler için açılır veya çevrimiçi yardım sağlayan bir <xref:System.Windows.Forms.HelpProvider> bileşen örneği oluşturur. Daha fazla bilgi için bkz. [HelpProvider bileşeni](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**'I**

Bir <xref:System.Drawing.Image> nesneleri koleksiyonunu yönetmek için yöntemler sağlayan bir <xref:System.Windows.Forms.ImageList> bileşen örneği oluşturur. Daha fazla bilgi için bkz. [ImageList bileşeni](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

İleti kuyrukları ile etkileşim kurmak için kullanabileceğiniz bir <xref:System.Messaging.MessageQueue> bileşen örneği oluşturur, sıralara ileti okuma ve sıralara ileti yazma, işlemleri işleme ve sıra yönetim görevleri gerçekleştirme dahil olmak üzere.

**PerformanceCounter**

Yeni kategoriler ve örnekler oluşturma, sayaçlardan değerleri okuma ve sayaç verilerinde hesaplamalar gerçekleştirme dahil olmak üzere Windows performans sayaçlarıyla etkileşim kurmak için kullanabileceğiniz bir <xref:System.Diagnostics.PerformanceCounter> bileşen örneği oluşturur.

**İşle**

Sisteminizdeki işlemlerle ilişkili verileri durdurmak, başlatmak ve işlemek için kullanabileceğiniz bir <xref:System.Diagnostics.Process> bileşen örneği oluşturur.

**SerialPort**

Zaman uyumlu ve olay odaklı g/ç, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlayan bir <xref:System.IO.Ports.SerialPort> bileşen örneği oluşturur.

**ServiceController**

Hizmetleri başlatma ve durdurma ve bunlara komut gönderme dahil olmak üzere mevcut hizmetleri yönetmek için kullanabileceğiniz bir <xref:System.ServiceProcess.ServiceController> bileşen örneği oluşturur.

**Timer**

Windows tabanlı uygulamalarınıza zamana dayalı işlevsellik eklemek için kullanabileceğiniz bir <xref:System.Windows.Forms.Timer> bileşen örneği oluşturur. Daha fazla bilgi için bkz. [süreölçer bileşeni](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Ayrıca, bu <xref:System.Timers.Timer> sunucu uygulamaları için en iyi duruma getirilmiş **araç kutusuna** ekleyebileceğiniz sistem tabanlı bir <xref:System.Timers.Timer> ve Windows Forms <xref:System.Windows.Forms.Timer> en uygun Windows Forms kullanım için uygundur.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms için kullanılacak denetimler](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Araç kutusu öğelerini, WPF bileşenlerini seçme](choose-toolbox-items-wpf-components.md)
- [Araç Kutusu](../../ide/reference/toolbox.md)
