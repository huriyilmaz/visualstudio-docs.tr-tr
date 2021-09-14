---
title: 'Nasıl kullanılır: Nesne Yöneticisi kitaplığına kitaplık | Microsoft Docs'
description: Sınıf Görünümü ve Object Browser gibi Visual Studio göz atma araçlarında sembolleri görüntüleyebilirsiniz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725056"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Nasıl kullanılır: Nesne yöneticisine kitaplık kaydetme
**Sınıf Görünümü**, **Object Browser**, **Çağrı Tarayıcısı** ve **Sembol** Sonuçlarını Bul gibi sembollere göz atma araçları, projeniz veya dış bileşenlerde sembolleri görüntülemenizi sağlar. Simgeler ad alanlarını, sınıfları, arabirimleri, yöntemleri ve diğer dil öğelerini içerir. Kitaplıklar bu sembolleri takip eder ve araçları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verilerle doldurmak için nesne yöneticisine gösterir.

 Nesne yöneticisi tüm kullanılabilir kitaplıkları takip eder. Sembol tarama araçları için semboller sağlamadan önce her kitaplığın nesne yöneticisine kaydolması gerekir.

 Bir VSPackage yüklenirken genellikle bir kitaplık kaydedebilirsiniz. Ancak, gerektiğinde başka bir zamanda yapılabilir. VSPackage kapatıldıktan sonra kitaplığın kaydını sildiyebilirsiniz.

 Bir kitaplığı kaydetmek için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> kullanın. Yönetilen kod kitaplığı için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> kullanın.

 Bir kitaplığın kaydını geri için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> kullanın.

 Nesne yöneticisine bir başvuru almak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> kimliğini yöntemine `GetService` iletir.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Nesne yöneticisiyle bir kitaplığı kaydetme ve kaydını geri kaydetme

### <a name="to-register-a-library-with-the-object-manager"></a>Bir kitaplığı nesne yöneticisine kaydetmek için

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

2. türünde bir nesneye başvuru alma <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> ve yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> çağırma.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Nesne yöneticisiyle bir kitaplığın kaydını silen

1. türünde bir nesneye başvuru alma <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> ve yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> çağırma.

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
- [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Nasıl kullanılır: Kitaplık tarafından sağlanan sembollerin listelerini nesne yöneticisine açığa çıkarma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
