---
title: 'Nasıl yapılır: hizmet sağlama | Microsoft Docs'
description: VSPackage, diğer VSPackages tarafından kullanılabilecek hizmetler sağlayabilir. bir vspackage 'ın Visual Studio bir hizmeti nasıl kaydedeceğini ve hizmeti nasıl ekleyeceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 11205634b75c3ae1892e7a4d964ae049ec50afbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050305"
---
# <a name="how-to-provide-a-service"></a>Nasıl yapılır: hizmet sağlama
VSPackage, diğer VSPackages tarafından kullanılabilecek hizmetler sağlayabilir. bir hizmet sağlamak için, bir vspackage hizmeti Visual Studio ve hizmeti eklemesi gerekir.

 <xref:Microsoft.VisualStudio.Shell.Package>Sınıfı hem hem de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> uygular <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> isteğe bağlı hizmetler sağlayan geri çağırma yöntemleri içerir.

 Hizmetler hakkında daha fazla bilgi için bkz. [Service Essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> vspackage boşaltılacak şekilde olduğunda Visual Studio, bir vspackage tarafından sağlanan hizmetlerin tüm istekleri teslim edilene kadar bekler. Bu hizmetler için yeni isteklere izin vermez. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>Kaldırma sırasında bir hizmeti iptal etmek için yöntemini açıkça çağırmamalıdır.

## <a name="implement-a-service"></a>Hizmet uygulama

1. vsıx projesi oluşturun (**dosya**  >  **yeni**  >  **Project**  >  **Visual C#**  >  **genişletilebilirlik**  >  **vsıx Project**).

2. Projeye VSPackage ekleyin. **Çözüm Gezgini** proje düğümünü seçin ve   >  **yeni öğe** ekle  >  **Visual C# öğeleri**  >  **genişletilebilirlik**  >  **Visual Studio paketi**' ne tıklayın.

3. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

   - Hizmeti tanımlayan bir arabirim. Bu arabirimlerin birçoğu boştur, yani bir yöntemi yoktur.

   - Hizmet arabirimini tanımlayan bir arabirim. Bu arabirim uygulanacak yöntemleri içerir.

   - Hem hizmeti hem de hizmet arabirimini uygulayan bir sınıf.

     Aşağıdaki örnek, üç türün temel bir uygulamasını gösterir. Hizmet sınıfının Oluşturucusu, hizmet sağlayıcısını ayarlamış olmalıdır.

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

### <a name="register-a-service"></a>Hizmet kaydetme

1. Bir hizmeti kaydetmek için <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmeti sağlayan VSPackage öğesine ekleyin. Aşağıda bir örnek verilmiştir:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Bu öznitelik `SMyService` Visual Studio kaydeder.

    > [!NOTE]
    > Aynı ada sahip başka bir hizmetin yerini alan bir hizmeti kaydetmek için öğesini kullanın <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Yalnızca bir hizmetin geçersiz kılınmasına izin verildiğini unutmayın.

### <a name="add-a-service"></a>Hizmet ekleme

1. VSPackage başlatıcısında hizmeti ekleyin ve hizmetleri oluşturmak için bir geri arama yöntemi ekleyin. Bu yöntemde yapılacak değişiklik aşağıda verilmiştir <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> :

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Hizmeti oluşturması ve döndürmesi gereken geri çağırma yöntemini veya oluşturuoluşturuoluşturulmadıysa null değerini uygulayın.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio, hizmet sağlama isteğini reddedebilir. Başka bir VSPackage hizmeti zaten sağlıyorsa bunu yapar.

3. Artık hizmeti alabilir ve yöntemlerini kullanabilirsiniz. Aşağıdaki örnek, başlatıcıdaki hizmetin kullanımını gösterir, ancak hizmeti, hizmeti kullanmak istediğiniz her yerde alabilir.

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

     Değeri `helloString` "Merhaba" olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [Service Essentials](../extensibility/internals/service-essentials.md)
