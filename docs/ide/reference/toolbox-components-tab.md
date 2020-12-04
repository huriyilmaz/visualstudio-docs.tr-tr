---
title: Araç Kutusu, Bileşenler Sekmesi
description: Araç kutusu penceresinin bileşenler sekmesinde bulacağınız bileşenler hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40ba84712a343a071d6213dc9cd985727fc20ebf
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560947"
---
# <a name="toolbox-components-tab"></a>Araç kutusu, bileşenler sekmesi

Windows Forms için Visual Basic ve C# tasarımcılarına ekleyebileceğiniz bileşenleri görüntüler. Ve bileşenleri gibi Visual Studio 'da bulunan .NET bileşenlerine ek olarak, <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> kendi veya üçüncü taraf bileşenlerinizi bu sekmeye ekleyebilirsiniz.

Bu sekmeyi göstermek için bir Windows Forms Tasarımcısı açın. **Görünüm**  >  **araç kutusunu** seçin. **Araç kutusu**' nda **Bileşenler** sekmesini seçin.

## <a name="components"></a>Bileşenler

**BackgroundWorker**

<xref:System.ComponentModel.BackgroundWorker>Ayrı ve adanmış bir iş parçacığında bir işlemi çalıştırabilede bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [BackgroundWorker Component](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

<xref:System.DirectoryServices.DirectoryEntry>Active Directory hiyerarşisindeki bir düğüm veya nesneyi kapsülleyen ve Active Directory hizmet sağlayıcılarıyla etkileşim kurmak için kullanılabilen bir bileşen örneği oluşturur.

**DirectorySearcher**

<xref:System.DirectoryServices.DirectorySearcher>Active Directory karşı sorguları gerçekleştirmek için kullanabileceğiniz bir bileşen örneği oluşturur.

**Bileþeni**

<xref:System.Windows.Forms.ErrorProvider>Son kullanıcıya, formdaki bir denetimin bir hata ile ilişkili bir hata olduğunu gösteren bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [ErrorProvider Component](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

<xref:System.Diagnostics.EventLog>Günlüğe olay yazma ve günlük verilerini okuma dahil olmak üzere sistem ve özel olay günlükleriyle etkileşim kurmak için kullanabileceğiniz bir bileşen örneği oluşturur.

**FileSystemWatcher**

Erişiminiz olan <xref:System.IO.FileSystemWatcher> herhangi bir dizin veya dosyadaki değişiklikleri izlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**HelpProvider**

<xref:System.Windows.Forms.HelpProvider>Denetimler için açılır veya çevrimiçi yardım sağlayan bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [HelpProvider bileşeni](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**'I**

<xref:System.Windows.Forms.ImageList>Bir nesne koleksiyonunu yönetmek için yöntemler sağlayan bir bileşen örneği oluşturur <xref:System.Drawing.Image> . Daha fazla bilgi için bkz. [ImageList bileşeni](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Sıralara ileti <xref:System.Messaging.MessageQueue> okuma ve sıralara ileti yazma, işlemleri işleme ve sıra yönetim görevleri gerçekleştirme dahil olmak üzere ileti kuyrukları ile etkileşim kurmak için kullanabileceğiniz bir bileşen örneği oluşturur.

**PerformanceCounter**

<xref:System.Diagnostics.PerformanceCounter>Yeni kategoriler ve örnekler oluşturma, sayaçlardan değerleri okuma ve sayaç verilerinde hesaplamalar gerçekleştirme dahil olmak üzere Windows performans sayaçlarıyla etkileşim kurmak için kullanabileceğiniz bir bileşen örneği oluşturur.

**İşleme**

<xref:System.Diagnostics.Process>Sisteminizdeki işlemlerle ilişkili verileri durdurmak, başlatmak ve işlemek için kullanabileceğiniz bir bileşen örneği oluşturur.

**SerialPort**

<xref:System.IO.Ports.SerialPort>Zaman uyumlu ve olay odaklı g/ç, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlayan bir bileşen örneği oluşturur.

**ServiceController**

<xref:System.ServiceProcess.ServiceController>Hizmetleri başlatma ve durdurma ve bunlara komut gönderme dahil olmak üzere mevcut hizmetleri yönetmek için kullanabileceğiniz bir bileşen örneği oluşturur.

**Zamanlayıcı**

<xref:System.Windows.Forms.Timer>Windows tabanlı uygulamalarınıza zamana dayalı işlevsellik eklemek için kullanabileceğiniz bir bileşen örneği oluşturur. Daha fazla bilgi için bkz. [süreölçer bileşeni](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Ayrıca, <xref:System.Timers.Timer> **araç kutusuna** ekleyebileceğiniz, <xref:System.Timers.Timer> sunucu uygulamaları için en iyi duruma getirilmiş bir sistem tabanlı sistem tabanlıdır ve Windows Forms <xref:System.Windows.Forms.Timer> Windows Forms kullanım için idealdir.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms için kullanılacak denetimler](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Araç Kutusu öğelerini, WPF bileşenlerini seçme](choose-toolbox-items-wpf-components.md)
- [Araç Kutusu](../../ide/reference/toolbox.md)
