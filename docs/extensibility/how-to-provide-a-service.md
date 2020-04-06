---
title: 'Nasıl Yapilir: Hizmet Sağlayın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710779"
---
# <a name="how-to-provide-a-service"></a>Nasıl yapilir: Hizmet sağlama
VSPackage, diğer VSPackage'ların kullanabileceği hizmetler sunabilir. Bir hizmet sağlamak için, bir VSPackage Visual Studio ile hizmet kayıt ve hizmet eklemek gerekir.

 Sınıf <xref:Microsoft.VisualStudio.Shell.Package> hem <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> uygular <xref:System.ComponentModel.Design.IServiceContainer>ve. <xref:System.ComponentModel.Design.IServiceContainer>isteğe bağlı hizmetler sağlayan geri arama yöntemleri içerir.

 Hizmetler hakkında daha fazla bilgi için [Hizmet temellerine](../extensibility/internals/service-essentials.md) bakın.

> [!NOTE]
> Bir VSPackage kaldırılmak üzereyken, Visual Studio bir VSPackage'ın sağladığı tüm hizmet talepleri teslim edilene kadar bekler. Bu hizmetler için yeni isteklere izin vermez. Boşaltma yaparken bir hizmeti <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> iptal etme yöntemini açıkça aramamalısınız.

## <a name="implement-a-service"></a>Bir hizmet uygulama

1. Bir VSIX projesi oluşturun (**Dosya** > **Yeni** > **Proje** > **Görsel C#** > **Genişletilebilirlik** > **VSIX Projesi**).

2. Projeye bir VSPackage ekleyin. **Çözüm Gezgini'ndeki** proje düğümünü seçin ve**Yeni öğe** > **Görsel C# Öğeleri** > **Genişletilebilirlik** > **Görsel Stüdyo Paketi'ni** **tıklatın.** > 

3. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

   - Hizmeti açıklayan bir arabirim. Bu arabirimlerin çoğu boş, yani hiçbir yöntemleri var.

   - Hizmet arabirimini açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.

   - Hem hizmet hem de hizmet arabirimini uygulayan bir sınıf.

     Aşağıdaki örnek, üç tür temel bir uygulama gösterir. Hizmet sınıfının oluşturucusu servis sağlayıcıyı ayarlamalıdır.

   ```csharp
   public class MyService : SMyService, IMyService
   {
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;
       private string myString;
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)
       {
           Trace.WriteLine(
                  "Constructing a new instance of MyService");
           serviceProvider = sp;
       }
       public void Hello()
       {
           myString = "hello";
       }
       public string Goodbye()
       {
          return "goodbye";
       }
   }
   public interface SMyService
   {
   }
   public interface IMyService
   {
       void Hello();
       string Goodbye();
   }

   ```

### <a name="register-a-service"></a>Bir hizmeti kaydetme

1. Bir hizmeti kaydetmek için, hizmeti sağlayan VSPackage'a ekleyin. <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Örnek aşağıda verilmiştir:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Bu öznitelik `SMyService` Visual Studio ile kaydeder.

    > [!NOTE]
    > Başka bir hizmeti aynı ada sahip olarak kaydeden <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>bir hizmeti kaydetmek için . Bir hizmetin yalnızca bir geçersiz kılınmasına izin verildiğini unutmayın.

### <a name="add-a-service"></a>Hizmet ekleme

1. VSPackage baş harflerinde, hizmeti ekleyin ve hizmetleri oluşturmak için bir geri arama yöntemi ekleyin. Yöntemde yapacağınız değişiklik <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> aşağıda veda edinebilirsiniz:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Hizmeti oluşturması ve döndürmesi gereken geri arama yöntemini uygulayın veya oluşturulamıyorsa geçersiz kılın.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio bir hizmet sağlama isteğini reddedebilir. Başka bir VSPackage zaten hizmet sağlarsa bunu yapar.

3. Şimdi hizmeti alabilir ve yöntemlerini kullanabilirsiniz. Aşağıdaki örnekte, hizmeti baş harflerinde kullanmak gösterilmektedir, ancak hizmeti kullanmak istediğiniz her yerde alabilirsiniz.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     Değeri "Merhaba" `helloString` olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapilir: Hizmet alın](../extensibility/how-to-get-a-service.md)
- [Kullanım ve hizmet sağlama](../extensibility/using-and-providing-services.md)
- [Hizmet esasları](../extensibility/internals/service-essentials.md)
