---
title: Yeniden düzenlemeyi yenidenC#Adlandır () | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667472"
---
# <a name="rename-refactoring-c"></a>Yeniden Düzenlemeyi (C#) yeniden adlandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Yeniden adlandırma** , Visual Studio tümleşik geliştirme ORTAMıNDA (IDE) alanlar, yerel değişkenler, Yöntemler, ad alanları, Özellikler ve türler gibi kod sembolleri için tanımlayıcıları yeniden adlandırmanın kolay bir yolunu sağlayan bir yeniden düzenleme özelliğidir. **Yeniden adlandırma** , açıklamalarda ve dizelerdeki adları değiştirmek, bir tanımlayıcının bildirimlerini ve çağrılarını değiştirmek için kullanılabilir.

> [!NOTE]
> Visual Studio için kaynak denetimi kullanırken, yeniden adlandırma yeniden düzenlemesi gerçekleştirmeyi denemeden önce kaynakların en son sürümünü alın.

 Yeniden düzenlemeyi yeniden adlandırma aşağıdaki Visual Studio özelliklerinden edinilebilir:

|Özellik|IDE 'de yeniden düzenleme davranışı|
|-------------|----------------------------------------|
|Kod Düzenleyicisi|Kod Düzenleyicisi 'nde, imleci belirli kod sembolleri türlerinde konumlandırdığınızda yeniden düzenlemeyi yeniden adlandırma kullanılabilir. İmleç bu konumdayken, klavye kısayolunu (CTRL + R, CTRL + R) yazarak veya akıllı bir etiketten, kısayol menüsünden veya yeniden **Düzenle** menüsünden **Yeniden Adlandır** komutunu seçerek **Yeniden Adlandır** komutunu çağırabilirsiniz.|
|Sınıf Görünümü|Sınıf Görünümü bir tanımlayıcı seçtiğinizde, yeniden adlandırma, kısayol menüsünde ve yeniden **Düzenle** menüsünden kullanılabilir.|
|Nesne Tarayıcısı|Nesne Tarayıcısı bir tanımlayıcı seçtiğinizde yeniden düzenleme yeniden adlandırma yalnızca yeniden **Düzenle** menüsünden kullanılabilir.|
|Windows Form Tasarımcısı Özellik Kılavuzu|Windows Form Tasarımcısı **özellik kılavuzunda** , bir denetimin adını değiştirmek bu denetim için bir yeniden adlandırma işlemi başlatır. **Yeniden Adlandır** iletişim kutusu görünmez.|
|Çözüm Gezgini|**Çözüm Gezgini**, kısayol menüsünde **yeniden adlandırma** komutu kullanılabilir. Seçilen kaynak dosya, sınıf adı dosya adı ile aynı olan bir sınıf içeriyorsa, bu komutu, kaynak dosyayı aynı anda yeniden adlandırmak ve yeniden adlandırma yeniden düzenlemesi yürütmek için kullanabilirsiniz.<br /><br /> Örneğin, varsayılan bir Windows tabanlı uygulama oluşturup Form1.cs olarak yeniden adlandırırsanız, kaynak dosya adı Form1.cs TestForm.cs olarak değişir ve bu sınıfa yapılan tüm başvurular TestForm olarak yeniden adlandırılacaktır. **Note:**  **Geri al** komutu (CTRL + Z), koddaki yeniden adlandırmayı yalnızca yeniden adlandır işlemini geri alır ve dosya adını özgün ada geri değiştirmez. <br /><br /> Seçilen kaynak dosya, adı dosya adı ile aynı olan bir sınıf içermiyorsa, **Çözüm Gezgini** ' deki **Yeniden Adlandır** komutu yalnızca kaynak dosyayı yeniden adlandırır ve yeniden adlandırma yeniden düzenleme işlemi yürütülmez.|

## <a name="rename-operations"></a>Yeniden adlandırma Işlemleri
 **Yeniden adlandırma**yürüttüğünüzde, yeniden düzenleme altyapısı, aşağıdaki tabloda açıklandığı gibi her bir kod sembolü için özel bir yeniden adlandırma işlemi gerçekleştirir.

|Kod simgesi|Yeniden adlandırma Işlemi|
|-----------------|----------------------|
|Alan|Alanın bildirimini ve kullanımlarını yeni adla değiştirir.|
|Yerel değişken|Değişkenin bildirim ve kullanımlarını yeni ad olarak değiştirir.|
|Yöntem|Yöntemin adını ve bu yönteme yapılan tüm başvuruları yeni adla değiştirir. **Note:**  Bir uzantı yöntemini yeniden adlandırdığınızda, Uzantı yönteminin statik bir yöntem veya örnek yöntemi olarak kullanılıp kullanılmadığına bakılmaksızın, yeniden adlandırma işlemi, kapsam içinde olan metodun tüm örneklerine yayar. Daha fazla bilgi için bkz. [Uzantı yöntemleri](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Ad Alanı|Ad alanının adını bildirimdeki yeni ad, tüm `using` deyimleri ve tam olarak nitelenmiş adlar olarak değiştirir. **Note:**  Bir ad alanını yeniden adlandırırken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, **Proje Tasarımcısı**'nın **uygulama** sayfasındaki **varsayılan ad alanı** özelliğini de güncelleştirir. Bu özellik, **Düzenle** menüsünden **geri al** seçeneği belirlenerek sıfırlanamaz. **Varsayılan ad alanı** özellik değerini sıfırlamak Için, **Proje Tasarımcısı**' nda özelliği değiştirmelisiniz. Daha fazla bilgi için bkz. [uygulama sayfası](../ide/reference/application-page-project-designer-csharp.md).|
|Özellik|Özelliğin bildirim ve kullanımlarını yeni ad olarak değiştirir.|
|Tür|Oluşturucu ve Yıkıcılar da dahil olmak üzere tüm bildirimleri ve türün tüm kullanımlarını yeni ad olarak değiştirir. Kısmi türler için, yeniden adlandırma işlemi tüm bölümlere yayılır.|

#### <a name="to-rename-an-identifier"></a>Bir tanımlayıcıyı yeniden adlandırmak için

1. @No__t_0 adlı bir konsol uygulaması oluşturun ve `Program` aşağıdaki örnek kodla değiştirin.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. İmleci yöntem bildiriminde ya da yöntem çağrısında `MethodB`.

3. Yeniden **Düzenle** menüsünde **Yeniden Adlandır**' ı seçin. **Yeniden Adlandır** iletişim kutusu görüntülenir.

     Ayrıca, imleci sağ tıklayıp bağlam menüsünde yeniden **Düzenle** ' yi işaret ettikten sonra yeniden adlandır ' **a tıklayarak** **Yeniden Adlandır** iletişim kutusunu görüntüleyebilirsiniz.

4. **Yeni ad** alanına `MethodC` yazın.

5. **Açıklamalarda ara** onay kutusunu seçin.

6. **Tamam**'a tıklayın.

7. **Değişiklikleri Önizle** Iletişim kutusunda **Uygula**' ya tıklayın.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Akıllı etiketleri kullanarak bir tanımlayıcıyı yeniden adlandırmak için

1. @No__t_0 adlı bir konsol uygulaması oluşturun ve `Program` aşağıdaki örnek kodla değiştirin.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. @No__t_0 bildiriminde, yöntem tanımlayıcısının üzerine yazın veya geri yazın. Bu tanımlayıcının altında akıllı bir etiket istemi görüntülenir.

    > [!NOTE]
    > Yalnızca bir tanımlayıcının bildiriminde Akıllı Etiketler ' i yeniden Düzenle yeniden düzenleme çağırabilirsiniz.

3. SHIFT + ALT + F10 klavye kısayolunu yazın ve ardından akıllı etiket menüsünü göstermek için aşağı oka basın.

     veya

     Akıllı etiketi göstermek için fare işaretçisini akıllı etiket isteminin üzerine taşıyın. Sonra fare işaretçisini akıllı etiketin üzerine taşıyın ve akıllı etiket menüsünü göstermek için aşağı oka tıklayın.

4. Kodunuzun değişikliklerinin önizlemesi olmadan yeniden adlandırmayı yeniden düzenlemeyi çağırmak için ' **\<identifer1 > ' öğesini ' \<identifier2 > ' olarak yeniden** Adlandır ' ı seçin. **@No__t_1identifer1 >** tüm başvuruları, **> \<identifier2**otomatik olarak güncelleştirilir.

     veya

     Kodunuzun değişikliklerinin önizlemesi ile yeniden adlandırma yeniden düzenlemesi 'ni çağırmak için Önizleme menü öğesiyle **Yeniden Adlandır** ' ı seçin. **Değişiklikleri Önizle** iletişim kutusu görüntülenir.

## <a name="remarks"></a>Açıklamalar

## <a name="renaming-implemented-or-overridden-members"></a>Uygulanan veya geçersiz kılınan üyeleri yeniden adlandırma
 Uygulayan/geçersiz kılan veya diğer türlerdeki Üyeler tarafından uygulanan/geçersiz kılınan bir üyeyi **yeniden adlandırdığınızda** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], yeniden adlandırma işleminin basamaklı güncelleştirmelere neden olacağını belirten bir iletişim kutusu görüntüler. **Devam**' a tıkladığınızda, yeniden düzenleme altyapısı, temel alınan ve yeniden adlandırılmakta olan üyeyle birlikte uygulayan/geçersiz kılan ilişkiler içeren türetilmiş türlerdeki tüm üyeleri yinelemeli olarak bulur ve yeniden adlandırır.

 Aşağıdaki kod örneği, Implements/geçersiz kılmalar ilişkilerine sahip Üyeler içerir.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 Önceki örnekte, `C.Method()` `Ibase.Method()` uyguladığından `C.Method()` yeniden adlandırılması `Ibase.Method()` de yeniden adlandırılır. Sonra, yeniden düzenleme motoru `Ibase.Method()` `Derived.Method()` tarafından uygulandığını ve `Derived.Method()` yeniden adlandırarak bir kez daha olduğunu görür. @No__t_1 `Base.Method()` geçersiz kılmadığından yeniden düzenleme motoru `Base.Method()` olarak yeniden adlandırmaz. Yeniden adlandırma altyapısı, **Yeniden Adlandır** iletişim kutusunda işaretlenen **yeniden yüklemeleri yeniden adlandır** ' a kadar burada duraklar.

 **Aşırı yüklemeleri yeniden adlandırma** Işaretlenirse, yeniden düzenleme motoru, `Derived.Method(int i)` tarafından geçersiz kılındığından ve `Base.Method()` bir `Base.Method(int i)` aşırı yüklemesi olduğundan, `Base.Method(int i)` `Derived.Method()` aşırı `Derived.Method(int i)`.

> [!NOTE]
> Başvurulan bir derlemede tanımlı bir üyeyi yeniden adlandırdığınızda, bir iletişim kutusu yeniden adlandırmanın derleme hatalarına neden olacağını açıklar.

## <a name="renaming-properties-of-anonymous-types"></a>Anonim türlerin özelliklerini yeniden adlandırma
 Anonim türlerde bir özelliği yeniden adlandırdığınızda, yeniden adlandırma işlemi aynı özelliklere sahip diğer anonim türlerdeki özelliklere yayılır. Aşağıdaki örneklerde bu davranış gösterilmektedir.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 Yukarıdaki kodda, aynı temel anonim türe sahip olduklarından `ID` yeniden adlandırılması her iki deyimde `ID` değiştirecek.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 Yukarıdaki kodda, `companyIDs` ve `orderIDs` aynı özelliklere sahip olmadığından, `ID` yeniden adlandırılması yalnızca bir `ID` örneğini yeniden adlandıracaktır.

## <a name="see-also"></a>Ayrıca Bkz.
 Yeniden [düzenlemeC#()](../csharp-ide/refactoring-csharp.md) [anonim türler](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)