---
title: Arka plan iş parçacığından UML modelini güncelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e6626faa09f1e38506c2d205d13caa9a3707fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659461"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Bir UML modelini arka plan iş parçacığı aracılığıyla güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen bir arka plan iş parçacığında modelde değişiklik yapmak faydalı olabilir. Örneğin, yavaş bir dış kaynaktan bilgi yüklüyorsanız, güncelleştirmeleri denetetmek için bir arka plan iş parçacığı kullanabilirsiniz. Bu, kullanıcının her güncelleştirmeyi gerçekleşir almaz görmesini sağlar.

 Ancak, UML mağazasının iş parçacığı güvenli olmadığı farkında olmalısınız. Aşağıdaki önlemler önemlidir:

- Bir modele veya diyagrama yönelik her güncelleştirme, Kullanıcı arabirimi (UI) iş parçacığında yapılmalıdır. <xref:System.Windows.Forms.Control.Invoke%2A> `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A> UI iş parçacığının gerçek güncelleştirmeleri gerçekleştirmesi için arka plan iş parçacığının kullanılması gerekir.

- Bir dizi değişikliği tek bir işlemde gruplandırdıysanız, işlem devam ederken kullanıcının modeli düzenlemesini engellemeniz önerilir. Aksi takdirde, Kullanıcı tarafından yapılan tüm düzenlemeler aynı işlemin bir parçası olur. Kullanıcının kalıcı iletişim kutusunu göstererek değişiklik yapmasını engelleyebilirsiniz. İsterseniz, iletişim kutusunda bir Iptal düğmesi sağlayabilirsiniz. Kullanıcı değişiklikleri yaptığı şekilde görebilir.

## <a name="example"></a>Örnek
 Bu örnek, bir modelde birkaç değişiklik yapmak için bir arka plan iş parçacığı kullanır. İş parçacığı çalışırken kullanıcıyı dışlamak için bir iletişim kutusu kullanılır. Bu basit örnekte, iletişim kutusunda Iptal düğmesi sağlanmaz. Ancak, bu özelliği eklemek kolay bir işlemdir.

#### <a name="to-run-the-example"></a>Örneği çalıştırmak için

1. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)bölümünde açıklandığı gibi bir C# projesinde komut işleyicisi oluşturun.

2. Projenin bu derlemelere başvurular içerdiğinden emin olun:

   - Microsoft. VisualStudio. mimari Turetools. Extensibility

   - Microsoft. VisualStudio. model. SDK. sürümünüze

   - Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze

   - Microsoft. VisualStudio. Uml. Interfaces

   - System. ComponentModel. Composition

   - System. Windows. Forms

3. Projeye **ProgressForm**adlı bir Windows formu ekleyin. Güncelleştirmelerin devam ettiğini belirten bir ileti görüntülenmelidir. Başka bir denetime sahip olmak zorunda değildir.

4. Adım 7 ' den sonra gösterilen kodu içeren bir C# dosyası ekleyin.

5. Projeyi derleyin ve çalıştırın.

    Yeni bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deneysel modda başlayacaktır.

6. Deneysel örneğinde bir UML sınıf diyagramı oluşturun veya açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

7. UML sınıf diyagramında herhangi bir yere sağ tıklayın ve **bırkaç UML sınıfı Ekle**' ye tıklayın.

   Birkaç yeni sınıf kutusu diyagramda, diğeri yarım saniyelik aralıklarla bir kez görünür.

```csharp
using System;
using System.ComponentModel;
using System.ComponentModel.Composition;
using System.Threading;
using System.Windows.Forms;

using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.Uml.Classes;

namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class UmlClassAdderCommand : ICommandExtension
  {

    [Import]
    IDiagramContext context { get; set; }

    [Import]
    ILinkedUndoContext linkedUndoContext { get; set; }

    // Called when the user runs the command.
    public void Execute(IMenuCommand command)
    {
      // The form that will exclude the user.
      ProgressForm form = new ProgressForm();

      // System.ComponentModel.BackgroundWorker is a
      // convenient way to run a background thread.
      BackgroundWorker worker = new BackgroundWorker();
      worker.WorkerSupportsCancellation = true;

      worker.DoWork += delegate(object sender, DoWorkEventArgs args)
      {
        // This block will be executed in a background thread.

        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;
        IModelStore store = diagram.ModelStore;
        const int CLASSES_TO_CREATE = 15;

        // Group all the changes together.
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))
        {
          for (int i = 1; i < CLASSES_TO_CREATE; i++)
          {
            if (worker.CancellationPending)
               return; // No commit - undo all.

            // Create model elements using the UI thread by using
            // the Invoke method on the progress form. Always
            // modify the model and diagrams from a UI thread.
            form.Invoke((MethodInvoker)(delegate
            {
              IClass newClass = store.Root.CreateClass();
              newClass.Name = string.Format("NewClass{0}", i);
              diagram.Display(newClass);
            }));

            // Sleep briefly so that we can watch the updates.
            Thread.Sleep(500);
          }

          // Commit the transaction or it will be rolled back.
          transaction.Commit();
        }
      };

      // Close the form when the thread completes.
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)
      {
        form.Close();
      };

      // Start the thread before showing the modal progress dialog.
      worker.RunWorkerAsync();

      // Show the form modally, parented on VS.
      // Prevents the user from making changes while in progress.
      form.ShowDialog();
    }

    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }

    public string Text
    {
      get { return "Add several classes"; }
    }
  }
}
```

#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Kullanıcının örnekteki iş parçacığını iptal edebilmesini sağlamak için

1. İlerleme iletişim kutusuna bir iptal düğmesi ekleyin.

2. İlerleme iletişim kutusuna aşağıdaki kodu ekleyin:

     `public event MethodInvoker Cancel;`

     `private void CancelButton_Click(object sender, EventArgs e)`

     `{`

     `Cancel();`

     `}`

3. Execute () yönteminde, formun oluşturulmasından sonra bu satırı ekleyin:

     `form.Cancel += delegate() { worker.CancelAsync(); };`

### <a name="other-methods-of-accessing-the-ui-thread"></a>UI iş parçacığına erişmenin diğer yöntemleri
 Bir iletişim kutusu oluşturmak istemiyorsanız, diyagramı görüntüleyen denetime erişebilirsiniz:

 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`

 `uiThreadHolder.Invoke()`Kullanıcı arabirimi iş parçacığında işlemleri gerçekleştirmek için kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 Modelleme diyagramında bir [menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
