---
title: Workflow Foundation projesi oluşturma
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8c3e4930376d2d2f9a6ee3334d8b164279d5ac2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597080"
---
# <a name="workflow-project-templates"></a>İş akışı proje şablonları

Visual Studio proje şablonlarını kullanarak Iş akışları, Windows Communication Foundation (WCF) iş akışı hizmetleri, özel etkinlikler ve özel etkinlik tasarımcıları oluşturabilirsiniz. Bu makalede, Visual Studio 'da kullanılabilir proje şablonlarıyla kitaplıkların ve uygulamaların nasıl oluşturulacağı açıklanır.

## <a name="create-a-workflow-project"></a>İş Akışı projesi Oluşturma

Visual Studio dört farklı Iş akışı proje şablonu sağlar:

- İş akışı konsol uygulaması

- WCF iş akışı hizmeti uygulaması

- Etkinlik kitaplığı

- Etkinlik Tasarımcısı kitaplığı

Bu şablonlara erişmek için önce Visual Studio 'nun **Windows Workflow Foundation** bileşenini yüklemeniz gerekir. Ayrıntılı yönergeler için bkz. [ınstall Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. **Windows Workflow Foundation** bileşenini yükledikten sonra **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

1. Bir iş akışı proje şablonu (örneğin, **Iş akışı konsol uygulaması** şablonu) arayın ve seçin.

1. Projeyi oluşturmak için devam edin.

   > [!NOTE]
   > Mevcut bir çözüme yeni bir proje eklemek istiyorsanız, Visual Studio 'da bu çözümü açın, **Çözüm Gezgini**' de çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

## <a name="workflow-console-app"></a>İş akışı konsol uygulaması

**Iş akışı konsol uygulaması** şablonunu seçerseniz, VISUAL Studio xaml 'de bir iş akışı tanımı oluşturur. İş Akışı Tasarımcısı açılır ve oluşturduğunuz iş akışının tuvali görüntülenir. Bir iş akışı oluşturmak için, etkinlik veya diğer iş akışı öğelerini **araç kutusundan** tasarım yüzeyine sürükleyin.

## <a name="wcf-workflow-service-app"></a>WCF iş akışı hizmeti uygulaması

**WCF Iş akışı hizmeti uygulama** şablonunu seçerseniz, Visual Studio bir HIZMET tanımını xaml olarak oluşturur. İş Akışı Tasarımcısı, <xref:System.Activities.Statements.Sequence> bir dizi ve etkinlik içeren bir etkinlikle Tasarım görünümüne açılır <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> .

## <a name="activity-library"></a>Etkinlik kitaplığı

**Etkinlik kitaplığı** şablonunu seçerseniz, VISUAL Studio xaml 'de bir etkinlik tanımı oluşturur. İş Akışı Tasarımcısı açılır ve özel etkinliğinizin tuvali görüntülenir. Bir etkinliği özel etkinliğinizden dahil etmek için **araç kutusu** ' ndan tasarım yüzeyine sürükleyin.

> [!NOTE]
> Özel etkinliğinizin gövdesinde yalnızca bir alt etkinliğe izin verilir. Ancak, bu alt etkinlik etkinlik veya etkinlik gibi bir bileşik etkinlik olabilir <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Flowchart> .

## <a name="activity-designer-library"></a>Etkinlik Tasarımcısı kitaplığı

**Etkinlik Tasarımcısı kitaplık** şablonunu seçerseniz, VISUAL Studio xaml 'de bir etkinlik Tasarımcısı tanımı ve arka plan kod uygulama dosyası oluşturur. İş Akışı Tasarımcısı açılır ve etkinlik tasarlayıcılarınızın tuvali görüntülenir. Windows Presentation Foundation (WPF) denetimlerini **araç kutusundan** tasarım yüzeyine sürükleyerek özel etkinlik tasarımcısında kullanın.

Özel bir etkinlik tasarımcısının nasıl uygulanacağı hakkında bir örnek için bkz. [nasıl yapılır: özel etkinlik Tasarımcısı oluşturma](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Özel etkinlik tasarımcıları, özel etkinlikler ve varsayılan .NET etkinlikleri için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Tasarım iş akışları (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
