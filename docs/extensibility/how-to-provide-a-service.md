---
title: 'Nasıl |: Hizmet | Microsoft Docs'
description: VSPackage, diğer VSPackage'ların kullanabileceği hizmetler sağlar. VSPackage'ın bir hizmeti Visual Studio nasıl ekley olduğunu öğrenin.
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
ms.openlocfilehash: a21a1dc08f0dcc47298e546520a85de3f4e3df8a3a0a563d173eb723531ecd37
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448283"
---
# <a name="how-to-provide-a-service"></a>Nasıl: Hizmet sağlama
VSPackage, diğer VSPackage'ların kullanabileceği hizmetler sağlar. Hizmet sağlamak için VSPackage'ın hizmeti Visual Studio kaydetmesi ve eklemesi gerekir.

 sınıfı <xref:Microsoft.VisualStudio.Shell.Package> hem hem de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 'i uygulayan bir sınıftır. <xref:System.ComponentModel.Design.IServiceContainer> <xref:System.ComponentModel.Design.IServiceContainer> , isteğe bağlı hizmetler sağlayan geri çağırma yöntemlerini içerir.

 Hizmetler hakkında daha fazla bilgi için [bkz. Hizmet temelleri.](../extensibility/internals/service-essentials.md)

> [!NOTE]
> BIR VSPackage'ın yüklemesi yüklenmek Visual Studio vsPackage'ın sağladığı tüm hizmetler için istekler teslim edilene kadar bekler. Bu hizmetler için yeni isteklere izin vermez. Kaldırma sırasında bir hizmeti iptal etmek <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> için yöntemini açıkça çağırmama gerekir.

## <a name="implement-a-service"></a>Hizmet uygulama

1. VSIX projesi oluşturma (**Visual** C# Project Dosya Yeni  >    >    >    >  **Genişletilebilirlik**  >  **VSIX Project**).

2. Projeye bir VSPackage ekleyin. Proje düğümünde proje düğümünü **seçin Çözüm Gezgini** Ekle Yeni öğe Visual C# Öğeleri Genişletilebilirlik   >    >    >    >  **Visual Studio Paketi'ne tıklayın.**

3. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

   - Hizmeti açıklayan bir arabirim. Bu arabirimlerin çoğu boştur, yani yöntemleri yoktur.

   - Hizmet arabirimini açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.

   - Hem hizmeti hem de hizmet arabirimini uygulayan bir sınıf.

     Aşağıdaki örnek, üç türün temel uygulamasını gösterir. Hizmet sınıfının oluşturucusu hizmet sağlayıcısını ayarlamalıdır.

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

1. Bir hizmeti kaydetmek için, hizmetini <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> sağlayan VSPackage'a ekleyin. Aşağıda bir örnek verilmiştir:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Bu öznitelik, `SMyService` Visual Studio.

    > [!NOTE]
    > Başka bir hizmeti aynı adla değiştiren bir hizmeti kaydetmek için <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> kullanın. Bir hizmetin yalnızca bir geçersiz kılmasına izin verilmiyor.

### <a name="add-a-service"></a>Hizmet ekleme

1. VSPackage başlatıcıda hizmeti ekleyin ve hizmetleri oluşturmak için bir geri çağırma yöntemi ekleyin. yönteminde yapılacak değişiklik şu <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> şekildedir:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Hizmeti oluşturması ve döndüren geri çağırma yöntemini veya oluşturulamazsa null değerini uygulama.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio hizmet sağlama isteğini reddeder. Başka bir VSPackage hizmeti zaten sağlarsa bunu yapar.

3. Artık hizmeti ve yöntemlerini kullanabilirsiniz. Aşağıdaki örnekte başlatıcıda hizmetinin kullanımı gösterilmiştir, ancak hizmeti kullanmak istediğiniz her yerde edinebilirsiniz.

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

     değerinin `helloString` "Hello" olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Hizmet al](../extensibility/how-to-get-a-service.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [Hizmet temelleri](../extensibility/internals/service-essentials.md)
