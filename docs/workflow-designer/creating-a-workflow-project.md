---
title: Workflow Foundation projesi oluşturma
description: Visual Studio'da kullanılabilen proje şablonlarıyla kitaplıklar ve uygulamalar Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: adb28a3ffd44e1cfcd744ab603d9c7e8555cafc3
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963726"
---
# <a name="workflow-project-templates"></a>İş akışı proje şablonları

İş Akışları, Windows Ve İletişim Temeli (WCF) iş akışı hizmetleri, özel etkinlikler ve özel etkinlik tasarımcıları oluşturmak için Visual Studio kullanabilirsiniz. Bu makalede, kitaplıklarda kullanılabilen proje şablonlarıyla kitaplıkların ve uygulamaların nasıl Visual Studio.

## <a name="create-a-workflow-project"></a>İş Akışı projesi Oluşturma

Visual Studio dört farklı İş Akışı proje şablonu sağlar:

- İş akışı konsol uygulaması

- WCF iş akışı hizmeti uygulaması

- Etkinlik kitaplığı

- Etkinlik tasarımcısı kitaplığı

Bu şablonlara erişmek için önce Windows **Workflow Foundation** bileşenini Visual Studio. Ayrıntılı yönergeler için bkz. [Workflow Foundation Windows yükleme.](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)

1. **Windows Workflow Foundation bileşenini** yükledikten sonra Dosya Yeni Dosya'Project.  >    >  

1. İş Akışı Konsolu Uygulama şablonu gibi bir iş akışı proje **şablonu için arama ve** seçme.

1. Projeyi oluşturmak için devam.

   > [!NOTE]
   > Mevcut bir çözüme yeni bir proje eklemek için bu çözümü Visual Studio'de açın, **Çözüm Gezgini'de** çözüme sağ tıklayın ve Yeni  >  **Ekle'yi Project.**

## <a name="workflow-console-app"></a>İş akışı konsol uygulaması

İş Akışı Konsolu Uygulaması **şablonunu seçerseniz,** Visual Studio XAML'de bir iş akışı tanımı oluşturur. Çalışma İş Akışı Tasarımcısı açılır ve oluşturduğunuz iş akışının tuvali görüntülenir. bir iş akışı oluşturmak için, etkinlikleri veya diğer iş akışı öğelerini **Araç Kutusu'dan tasarım** yüzeyine sürükleyin.

## <a name="wcf-workflow-service-app"></a>WCF iş akışı hizmeti uygulaması

WCF İş Akışı **Hizmet Uygulaması şablonunu seçerseniz,** Visual Studio XAML olarak bir hizmet tanımı oluşturur. Bu İş Akışı Tasarımcısı, ve etkinliklerini içeren <xref:System.Activities.Statements.Sequence> bir etkinlikle tasarım <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> görünümüne açılır.

## <a name="activity-library"></a>Etkinlik kitaplığı

Etkinlik Kitaplığı şablonunu **seçerseniz,** Visual Studio XAML'de bir etkinlik tanımı oluşturur. İş Akışı Tasarımcısı özel etkinliğiniz için tuval açılır ve görüntülenir. Bir etkinliği araç **kutusundan tasarım** yüzeyine sürükleyerek özel etkinliğinize dahil edin.

> [!NOTE]
> Özel etkinliğinizin gövdesinde yalnızca bir alt etkinlik izin verilir. Ancak bu alt etkinlik, etkinlik veya etkinlik gibi bileşik <xref:System.Activities.Statements.Sequence> bir etkinlik <xref:System.Activities.Statements.Flowchart> olabilir.

## <a name="activity-designer-library"></a>Etkinlik tasarımcısı kitaplığı

Etkinlik Tasarımcısı Kitaplığı **şablonunu seçerseniz,** Visual Studio XAML'de bir etkinlik tasarımcısı tanımı ve arka arkasındaki kod uygulaması dosyası oluşturur. Etkinlik İş Akışı Tasarımcısı açılır ve etkinlik tasarımcınız için tuval görüntülenir. Araç Windows Presentation Foundation (WPF) **denetimlerini özel** etkinlik tasarımcısında kullanmak için araç kutusundan tasarım yüzeyine sürükleyin.

Özel etkinlik tasarımcısı uygulama örneği için bkz. [Nasıl kullanılır: Özel etkinlik tasarımcısı oluşturma.](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)

> [!NOTE]
> Özel etkinlik tasarımcıları özel etkinlikler ve varsayılan .NET etkinlikleri için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [İş akışlarını tasarlama (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
