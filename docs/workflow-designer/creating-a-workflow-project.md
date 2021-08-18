---
title: Workflow Foundation projesi oluşturma
description: Visual Studio ' de kullanılabilir proje şablonlarıyla kitaplık ve uygulama oluşturmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155232"
---
# <a name="workflow-project-templates"></a>İş akışı proje şablonları

Visual Studio proje şablonları kullanarak iş akışları, Windows Communication Foundation (WCF) iş akışı hizmetleri, özel etkinlikler ve özel etkinlik tasarımcıları oluşturabilirsiniz. Bu makalede, Visual Studio ' de kullanılabilir proje şablonlarıyla kitaplıklar ve uygulamalar oluşturma açıklanır.

## <a name="create-a-workflow-project"></a>İş Akışı projesi Oluşturma

Visual Studio dört farklı iş akışı proje şablonu sağlar:

- İş akışı konsol uygulaması

- WCF iş akışı hizmeti uygulaması

- Etkinlik kitaplığı

- Etkinlik Tasarımcısı kitaplığı

bu şablonlara erişmek için önce Visual Studio **Windows Workflow Foundation** bileşenini yüklemeniz gerekir. ayrıntılı yönergeler için bkz. [ınstall Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. **Windows Workflow Foundation** bileşenini yükledikten sonra **dosya**  >  **yeni**  >  **Project**' ni seçin.

1. Bir iş akışı proje şablonu (örneğin, **Iş akışı konsol uygulaması** şablonu) arayın ve seçin.

1. Projeyi oluşturmak için devam edin.

   > [!NOTE]
   > mevcut bir çözüme yeni bir proje eklemek istiyorsanız, bu çözümü Visual Studio açın, **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

## <a name="workflow-console-app"></a>İş akışı konsol uygulaması

**iş akışı konsol uygulaması** şablonunu seçerseniz, Visual Studio XAML 'de bir iş akışı tanımı oluşturur. İş Akışı Tasarımcısı açılır ve oluşturduğunuz iş akışının tuvali görüntülenir. Bir iş akışı oluşturmak için, etkinlik veya diğer iş akışı öğelerini **araç kutusundan** tasarım yüzeyine sürükleyin.

## <a name="wcf-workflow-service-app"></a>WCF iş akışı hizmeti uygulaması

**WCF iş akışı hizmeti uygulama** şablonunu seçerseniz, Visual Studio XAML olarak bir hizmet tanımı oluşturur. İş Akışı Tasarımcısı, <xref:System.Activities.Statements.Sequence> bir dizi ve etkinlik içeren bir etkinlikle Tasarım görünümüne açılır <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> .

## <a name="activity-library"></a>Etkinlik kitaplığı

**etkinlik kitaplığı** şablonunu seçerseniz Visual Studio XAML 'de bir etkinlik tanımı oluşturur. İş Akışı Tasarımcısı açılır ve özel etkinliğinizin tuvali görüntülenir. Bir etkinliği özel etkinliğinizden dahil etmek için **araç kutusu** ' ndan tasarım yüzeyine sürükleyin.

> [!NOTE]
> Özel etkinliğinizin gövdesinde yalnızca bir alt etkinliğe izin verilir. Ancak, bu alt etkinlik etkinlik veya etkinlik gibi bir bileşik etkinlik olabilir <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Flowchart> .

## <a name="activity-designer-library"></a>Etkinlik Tasarımcısı kitaplığı

**etkinlik tasarımcısı kitaplık** şablonunu seçerseniz, Visual Studio XAML 'de bir etkinlik tasarımcısı tanımı ve arka plan kod uygulama dosyası oluşturur. İş Akışı Tasarımcısı açılır ve etkinlik tasarlayıcılarınızın tuvali görüntülenir. Windows Presentation Foundation (WPF) denetimlerini **araç kutusundan** tasarım yüzeyine sürükleyerek özel etkinlik tasarımcısında kullanın.

Özel bir etkinlik tasarımcısının nasıl uygulanacağı hakkında bir örnek için bkz. [nasıl yapılır: özel etkinlik Tasarımcısı oluşturma](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Özel etkinlik tasarımcıları, özel etkinlikler ve varsayılan .NET etkinlikleri için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Tasarım iş akışları (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
