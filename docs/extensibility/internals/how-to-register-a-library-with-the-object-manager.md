---
title: 'Nasıl yapılır: bir kitaplığı nesne yöneticisiyle kaydetme | Microsoft Docs'
description: Sınıf Görünümü ve Nesne Tarayıcısı gibi gözatma araçlarındaki sembolleri görüntüleyebilmeniz için Visual Studio nesne yöneticisiyle bir kitaplığı kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c70a59cd6510b761ce1cf44bc3d6d66d5766efe5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137721"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Nasıl yapılır: bir kitaplığı nesne yöneticisiyle kaydetme
**Sınıf görünümü**, **nesne tarayıcısı** **çağrı tarayıcısı** ve **sembol sonuçları bulma** gibi semboller-tarama araçları, projenizdeki veya dış bileşenlerdeki sembolleri görüntülemenizi sağlar. Semboller, ad alanları, sınıflar, arabirimler, Yöntemler ve diğer dil öğelerini içerir. Kitaplıklar bu sembolleri izler ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] araçları verilerle dolduran nesne Yöneticisi 'nde kullanıma sunar.

 Nesne Yöneticisi kullanılabilir tüm kitaplıkları izler. Sembol tarama araçları için semboller sağlamadan önce her kitaplığın nesne Yöneticisi ile kaydolması gerekir.

 Genellikle, bir VSPackage yüklendiğinde bir kitaplığı kaydedersiniz. Ancak, gerektiğinde başka bir zamanda yapılabilir. VSPackage kapandığında kitaplığın kaydını kaldırmanız gerekir.

 Bir kitaplığı kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> yöntemini kullanın. Yönetilen kod kitaplığı için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemini kullanın.

 Bir kitaplığın kaydını silmek için yöntemini kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .

 Nesne yöneticisine bir başvuru almak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> hizmet kimliğini `GetService` metoduna geçirin.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Nesne Yöneticisi ile bir kitaplığı kaydetme ve kaydını silme

### <a name="to-register-a-library-with-the-object-manager"></a>Bir kitaplığı nesne Yöneticisi ile kaydetmek için

1. Bir kitaplık oluşturun.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Türünün bir nesnesine bir başvuru alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi çağırın.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Bir kitaplığın nesne yöneticisiyle kaydını silmek için

1. Türünün bir nesnesine bir başvuru alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> yöntemi çağırın.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Destek sembolü-tarama araçları](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Nasıl yapılır: kitaplık tarafından nesne yöneticisine sunulan simgelerin listesini kullanıma sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
