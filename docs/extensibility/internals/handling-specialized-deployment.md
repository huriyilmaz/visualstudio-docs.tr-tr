---
title: Özelleştirilmiş dağıtımı işleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploying applications [Visual Studio SDK]
- specialized deployment
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c54b98c7bc7341a09fee9e6e5d0cc6860f4254f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848951"
---
# <a name="handle-specialized-deployment"></a>Özelleştirilmiş dağıtımı işle
Dağıtım, projeler için isteğe bağlı bir işlemdir. Örneğin, bir Web projesi, projenin bir Web sunucusunu güncelleştirmesine izin vermek için bir dağıtımı destekler. Benzer şekilde, **akıllı bir cihaz** projesi, yerleşik bir uygulamayı hedef cihaza kopyalamak için bir dağıtımı destekler. Proje alt türleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> arabirimini uygulayarak özelleştirilmiş dağıtım davranışı sağlayabilir. Bu arabirim, dağıtım işlemlerinin bir bütün kümesini tanımlar:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>

  Gerçek dağıtım işlemi, kullanıcı etkileşimine daha da fazla yanıt vermek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yapmak için ayrı iş parçacığında gerçekleştirilmelidir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> tarafından verilen Yöntemler, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tarafından zaman uyumsuz olarak adlandırılır ve arka planda çalışır, böylece ortam herhangi bir zamanda bir dağıtım işleminin durumunu sorgulayabilir veya gerekirse işlemi durdurabilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> arabirimi dağıtım işlemleri, Kullanıcı Dağıt komutunu seçtiğinde ortam tarafından çağırılır.

  Bir dağıtım işleminin başladığını veya sonlandırılacağını ortama bildirmek için, proje alt türünün <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A> yöntemlerini çağırması gerekir.

## <a name="to-handle-a-specialized-deployment-by-a-subtype-project"></a>Bir alt tür projesi tarafından özelleştirilmiş bir dağıtımı işlemek için

- Dağıtım durumu olaylarının bildirimlerini almak için ortamı kaydetmek üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A> yöntemini uygulayın.

    ```vb
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _
                                               ByRef pdwCookie As UInteger) As Integer

        If pIVsDeployStatusCallback Is Nothing Then
            Throw New ArgumentNullException("pIVsDeployStatusCallback")
        End If

        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)
        Return VSConstants.S_OK

    End Function
    ```

    ```csharp
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,
                                          out uint pdwCookie)
    {
        if (pIVsDeployStatusCallback == null)
            throw new ArgumentNullException("pIVsDeployStatusCallback");

        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);
        return VSConstants.S_OK;
    }

    ```

- Dağıtım durumu olaylarının bildirimlerini almak için ortamın kaydını iptal etmek üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A> yöntemini uygulayın.

    ```vb
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer
        adviseSink.RemoveAt(dwCookie)
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int UnadviseDeployStatusCallback(uint dwCookie)
    {
        adviseSink.RemoveAt(dwCookie);
        return VSConstants.S_OK;
    }

    ```

- Uygulamanıza özgü işleme işlemini gerçekleştirmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A> yöntemini uygulayın.  Bu yöntem, genellikle veritabanı dağıtımı için kullanılır.

    ```vb
    Public Function Commit(ByVal dwReserved As UInteger) As Integer
        'Implement commit operation here.
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int Commit(uint dwReserved)
    {
         //Implement commit operation here.
         return VSConstants.S_OK;
    }

    ```

- Geri alma işlemi gerçekleştirmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A> yöntemini uygulayın. Bu yöntem çağrıldığında dağıtım projesinin, değişiklikleri geri almak ve projenin durumunu geri yüklemek için uygun olan her şeyi yapması gerekir. Bu yöntem, genellikle veritabanı dağıtımı için kullanılır.

    ```vb
    Public Function Commit(ByVal dwReserved As UInteger) As Integer
        'Implement commit operation here.
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int Rollback(uint dwReserved)
    {
        //Implement Rollback operation here.
        return VSConstants.S_OK;
    }

    ```

- Bir projenin bir dağıtım işlemini başlatıp başlatamamadığını öğrenmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A> yöntemini uygulayın.

    ```vb
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then
            pfSupported(0) = 1
        End If
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then
            pfReady(0) = 0
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then
                pfReady(0) = 1
            End If
        End If
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)
    {
        if (pfSupported != null && pfSupported.Length >0)
            pfSupported[0] = 1;
        if (pfReady != null && pfReady.Length >0)
        {
            pfReady[0] = 0;
            if (deploymentThread != null && !deploymentThread.IsAlive)
                pfReady[0] = 1;
        }
        return VSConstants.S_OK;
    }

    ```

- Dağıtım işleminin başarıyla tamamlanıp tamamlanmadığını anlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A> yöntemini uygulayın.

    ```vb
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer
        pfDeployDone = 1
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            pfDeployDone = 0
        End If
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int QueryStatusDeploy(out int pfDeployDone)
    {
        pfDeployDone = 1;
        if (deploymentThread != null && deploymentThread.IsAlive)
            pfDeployDone = 0;
        return VSConstants.S_OK;
    }

    ```

- Ayrı bir iş parçacığında dağıtım işlemine başlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A> yöntemini uygulayın. `Deploy` yöntemi içinde uygulamanızın dağıtımına özgü kodu yerleştirin.

    ```vb
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer
        If pIVsOutputWindowPane Is Nothing Then
            Throw New ArgumentNullException("pIVsOutputWindowPane")
        End If

        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")
        End If

        outputWindow = pIVsOutputWindowPane

        ' Notify that deployment is about to begin and see if any user wants to cancel.
        If (Not NotifyStart()) Then
            Return VSConstants.E_ABORT
        End If

        operationCanceled = False

        ' Create and start our thread
        deploymentThread = New Thread(AddressOf Me.Deploy)
        deploymentThread.Name = "Deployment Thread"
        deploymentThread.Start()

        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)
    {
        if (pIVsOutputWindowPane == null)
            throw new ArgumentNullException("pIVsOutputWindowPane");

        if (deploymentThread != null && deploymentThread.IsAlive)
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");

        outputWindow = pIVsOutputWindowPane;

        // Notify that deployment is about to begin and see if any user wants to cancel.
        if (!NotifyStart())
            return VSConstants.E_ABORT;

        operationCanceled = false;

        // Create and start our thread
        deploymentThread = new Thread(new ThreadStart(this.Deploy));
        deploymentThread.Name = "Deployment Thread";
        deploymentThread.Start();

        return VSConstants.S_OK;
    }

    ```

- Dağıtım işlemini durdurmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A> yöntemini uygulayın. Bu yöntem, bir Kullanıcı dağıtım işlemi sırasında **iptal** düğmesine bastığında çağrılır.

    ```vb
    Public Function StopDeploy(ByVal fSync As Integer) As Integer
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            Return VSConstants.S_OK
        End If

        outputWindow.OutputStringThreadSafe("Canceling deployment")
        operationCanceled = True
        If fSync <> 0 Then
            ' Synchronous request, wait for the thread to terminate.
            If (Not deploymentThread.Join(10000)) Then
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")
                deploymentThread.Abort()
            End If
        End If

        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int StopDeploy(int fSync)
    {
        if (deploymentThread != null && deploymentThread.IsAlive)
            return VSConstants.S_OK;

        outputWindow.OutputStringThreadSafe("Canceling deployment");
        operationCanceled = true;
        if (fSync != 0)
        {
            // Synchronous request, wait for the thread to terminate.
            if (!deploymentThread.Join(10000))
            {
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");
                deploymentThread.Abort();
            }
        }

        return VSConstants.S_OK;
    }

    ```

> [!NOTE]
> Bu konuda sağlanan tüm kod örnekleri, [VSSDK örneklerindeki](https://github.com/Microsoft/VSSDK-Extensibility-Samples)daha büyük bir örneğin parçalarından oluşur.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje alt türleri](../../extensibility/internals/project-subtypes.md)
