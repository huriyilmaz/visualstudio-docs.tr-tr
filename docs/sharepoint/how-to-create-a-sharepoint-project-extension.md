---
title: 'Nasıl SharePoint Project: SharePoint Project Uzantısı | Microsoft Docs'
description: Bir proje uzantısının nasıl oluşturularak, SharePoint'da açık olan herhangi bir proje için işlev ekley Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/28/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 63bfc09edca9a87df95893758ffe4a6a8c85a465eb8cb23cc6c7d97416361eea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352948"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Nasıl yapabilirsiniz: SharePoint proje uzantısı oluşturma
  Uygulama içinde açık olan herhangi bir proje için işlev eklemek SharePoint proje uzantısı Visual Studio. Daha fazla bilgi için [bkz. SharePoint proje sistemini genişletme.](../sharepoint/extending-the-sharepoint-project-system.md)

### <a name="to-create-a-project-extension"></a>Proje uzantısı oluşturmak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Arabirimi uygulayan bir sınıf <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> oluşturun.

4. sınıfına <xref:System.ComponentModel.Composition.ExportAttribute> ekleyin. Bu öznitelik, Visual Studio bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> öznitelik oluşturucuya ilet.

5. yöntemi uygulamanıza, uzantının davranışını tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> *projectService* parametresinin üyelerini kullanın. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> arabirimde tanımlanan olaylara erişim sağlayan bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> nesnedir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde, arabirim tarafından tanımlanan proje olaylarının çoğunu SharePoint basit bir proje uzantısının nasıl oluşturularak ilgili bilgiler <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> ve bilgiler yer almaktadır. Kodu test etmek için içinde bir SharePoint proje oluşturun ve ardından çözüme daha fazla proje ekleyin, proje özellik değerlerini değiştirebilir veya bir projeyi silebilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] veya hariç tutabilirsiniz. Uzantı, Çıkış penceresine ve Hata Listesi penceresine iletiler **yazarak** olayları **size** bilgi verir.

  ```vb
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace
    ```

    ```csharp
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }
  ```

Bu örnekte, SharePoint proje hizmeti penceresine ve Hata Listesi **penceresine** yazmak için **aşağıdaki örnek iletiyi** kullanır. Daha fazla bilgi için [bkz. SharePoint proje hizmeti.](../sharepoint/using-the-sharepoint-project-service.md)

 ve olaylarını işlemeyi gösteren örnekler için bkz. Nasıl kullanılır: Projelerde SharePoint kısayol menü öğesi ekleme ve Nasıl kullanılır: Projelerine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> SharePoint [ekleme.](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md) [](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'deki SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Nasıl yapabilirsiniz: Projelerinize kısayol menü SharePoint ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Nasıl SharePoint: SharePoint ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Adım adım kılavuz: SharePoint proje uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
