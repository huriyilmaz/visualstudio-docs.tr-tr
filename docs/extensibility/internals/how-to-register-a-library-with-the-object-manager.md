---
title: 'Nasıl Yapilir: Kitaplığı Nesne Yöneticisine Kaydedin | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707938"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Nasıl yapilir: Kitaplığı nesne yöneticisine kaydedin
**Sınıf Görünümü,** **Nesne Tarayıcısı,** **Tarayıcıyı Arama** ve Sembol Sonuçlarını **Bul**gibi sembollere göz atma araçları, projenizdeki veya harici bileşenlerdeki sembolleri görüntülemenizi sağlar. Semboller ad boşluklarını, sınıfları, arabirimleri, yöntemleri ve diğer dil öğelerini içerir. Kitaplıklar bu sembolleri izler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve araçları verilerle dolduran nesne yöneticisine maruz bırakır.

 Nesne yöneticisi kullanılabilir tüm kitaplıkları izler. Her kitaplık, sembol tarama araçları için semboller sağlamadan önce nesne yöneticisine kaydolmalıdır.

 Genellikle, vspackage yüklendiğinde kitaplığı kaydedersiniz. Ancak, gerektiğinde başka bir zamanda yapılabilir. VSPackage kapandığında kitaplığın kaydını sayılabilirsiniz.

 Kitaplığı kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> yöntemi kullanın. Yönetilen kod kitaplığı için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi kullanın.

 Kitaplığın kaydını çıkarmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> için yöntemi kullanın.

 Nesne yöneticisine <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>başvuruda bulunulmak için <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> servis kimliğini `GetService` yönteme geçirin.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Kitaplığı nesne yöneticisine kaydettirme ve silme

### <a name="to-register-a-library-with-the-object-manager"></a>Kitaplığı nesne yöneticisine kaydetmek için

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

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> Türdeki bir nesneye başvuru alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> ve yöntemi çağırın.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Kitaplığı nesne yöneticisiyle birlikte çıkarmak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> Türdeki bir nesneye başvuru alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> ve yöntemi çağırın.

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
- [Eski dil hizmeti genişletilebilirlik](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Nasıl verilir: Kitaplık tarafından sağlanan sembollerin listelerini nesne yöneticisine göster](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
