---
title: Microsoft. VisualStudio. TestTools. CppUnitTestFramework 'Ü kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657178"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, `Microsoft::VisualStudio::CppUnitTestFramework` ad alanının ortak üyelerini listeler.

 Üst bilgi dosyaları _VisualStudio2012 [x86] InstallFolder_ **\Vc\unittest\ınclude** klasöründe bulunur.

 Lib dosyaları _VisualStudio2012 [x86] InstallFolder_ **\Vc\unittest\lib** klasöründe bulunur.

## <a name="BKMK_In_this_topic"></a>Bu konuda
 [CppUnitTest. h](#BKMK_CppUnitTest_h)

- [Test sınıfları ve yöntemleri oluşturma](#BKMK_Create_test_classes_and_methods)

- [Başlatma ve Temizleme](#BKMK_Initialize_and_cleanup)

  - [Test yöntemleri](#BKMK_Test_methods)

  - [Test sınıfları](#BKMK_Test_classes)

  - [Test modülleri](#BKMK_Test_modules)

- [Test öznitelikleri oluşturma](#BKMK_Create_test_attributes)

  - [Test yöntemi öznitelikleri](#BKMK_Test_method_attributes)

  - [Test sınıfı öznitelikleri](#BKMK_Test_class_attributes)

  - [Test modülü öznitelikleri](#BKMK_Test_module_attributes)

  - [Önceden tanımlanmış öznitelikler](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert. h](#BKMK_CppUnitTestAssert_h)

  - [Genel onaylar](#BKMK_General_Asserts)

    - [Eşittir](#BKMK_General_Are_Equal)

    - [Eşit değildir](#BKMK_General_Are_Not_Equal)

    - [Aynı](#BKMK_General_Are_Same)

    - [Aynı değil](#BKMK_General_Are_Not_Same)

    - [Null](#BKMK_General_Is_Null)

    - [Null değil](#BKMK_General_Is_Not_Null)

    - [Doğru](#BKMK_General_Is_True)

    - [Yanlış](#BKMK_General_Is_False)

    - [Neden](#BKMK_General_Fail)

  - [Windows Çalışma Zamanı onayları](#BKMK_WinRT_Asserts)

    - [Eşittir](#BKMK_WinRT_Are_Equal)

    - [Aynı](#BKMK_WinRT_Are_Same)

    - [Eşit değildir](#BKMK_WinRT_Are_Not_Equal)

    - [Aynı değil](#BKMK_WinRT_Are_Not_Same)

    - [Null](#BKMK_WinRT_Is_Null)

    - [Null değil](#BKMK_WinRT_Is_Not_Null)

  - [Özel durum onayları](#BKMK_Exception_Asserts)

    - [Özel durum bekliyor](#BKMK_Expect_Exception)

      [Cppunittestgünlükçü. h](#BKMK_CppUnitTestLogger_h)

    - [Medi](#BKMK_Logger)

    - [Ileti yaz](#BKMK_Write_Message)

## <a name="BKMK_CppUnitTest_h"></a>CppUnitTest. h

### <a name="BKMK_Create_test_classes_and_methods"></a>Test sınıfları ve yöntemleri oluşturma

```cpp
TEST_CLASS(className)
```

 Test yöntemleri içeren her sınıf için gereklidir. *ClassName* bir test sınıfı olarak tanımlar. `TEST_CLASS`, namescape Scope 'ta bildirilmelidir.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 *MethodName* öğesini bir test yöntemi olarak tanımlar. `TEST_METHOD`, yöntemin sınıfının kapsamında bildirilmelidir.

### <a name="BKMK_Initialize_and_cleanup"></a>Başlatma ve Temizleme

#### <a name="BKMK_Test_methods"></a>Test yöntemleri

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 *MethodName* öğesini, her test yöntemi çalıştırılmadan önce çalışan bir yöntem olarak tanımlar. `TEST_METHOD_INITIALIZE`, test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfında tanımlanmalıdır.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 *MethodName* öğesini her test yöntemi çalıştırıldıktan sonra çalışan bir yöntem olarak tanımlar. `TEST_METHOD_CLEANUP`, test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

#### <a name="BKMK_Test_classes"></a>Test sınıfları

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 *MethodName* öğesini her test sınıfı oluşturulduktan sonra çalışan bir yöntem olarak tanımlar. `TEST_CLASS_INITIALIZE`, test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 *MethodName* öğesini her test sınıfı oluşturulduktan sonra çalışan bir yöntem olarak tanımlar. `TEST_CLASS_CLEANUP`, test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

#### <a name="BKMK_Test_modules"></a>Test modülleri

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Bir modül yüklendiğinde çalıştırılan *MethodName* yöntemini tanımlar. `TEST_MODULE_INITIALIZE`, test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirilmelidir.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Bir modül kaldırıldığında çalıştırılan *MethodName* yöntemini tanımlar. `TEST_MODULE_CLEANUP`, test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirilmelidir.

### <a name="BKMK_Create_test_attributes"></a>Test öznitelikleri oluşturma

#### <a name="BKMK_Test_method_attributes"></a>Test yöntemi öznitelikleri

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Bir veya daha fazla `TEST_METHOD_ATTRIBUTE` makrolarıyla tanımlanan öznitelikleri *testClassName*test yöntemine ekler.

 @No__t_0 makrosu, *ÖznitelikAdı* ve *AttributeValue*değeri olan bir özniteliği tanımlar.

#### <a name="BKMK_Test_class_attributes"></a>Test sınıfı öznitelikleri

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 *TestClassName*test sınıfına bir veya daha fazla `TEST_CLASS_ATTRIBUTE` makrolarıyla tanımlanan öznitelikleri ekler.

 @No__t_0 makrosu, *ÖznitelikAdı* ve *AttributeValue*değeri olan bir özniteliği tanımlar.

#### <a name="BKMK_Test_module_attributes"></a>Test modülü öznitelikleri

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 *TestModuleName*test modülüne bir veya daha fazla `TEST_MODULE_ATTRIBUTE` makrolarıyla tanımlanan öznitelikleri ekler.

 @No__t_0 makrosu, *ÖznitelikAdı* ve *AttributeValue*değeri olan bir özniteliği tanımlar.

#### <a name="BKMK_Pre_defined_attributes"></a>Önceden tanımlanmış öznitelikler
 Önceden tanımlanmış bu öznitelik makroları, yukarıda açıklanan `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` veya `TEST_MODULE_ATTRIBUTE` makrolar için değiştirilebilir.

```cpp
TEST_OWNER(ownerAlias)
```

 Name `Owner` ve *ownerAlias*özniteliği değeri olan bir özniteliği tanımlar.

```cpp
TEST_DESCRIPTION(description)
```

 @No__t_0 adı ve *Açıklama*özniteliği değeri olan bir özniteliği tanımlar.

```cpp
TEST_PRIORITY(priority)
```

 @No__t_0 adı ve *Öncelik*değeri olan özniteliği tanımlar.

```cpp
TEST_WORKITEM(workitem)
```

 Name `WorkItem` ve *WorkItem*özniteliği değeri olan bir özniteliği tanımlar.

```cpp
TEST_IGNORE()
```

 @No__t_0 adı ve `true` öznitelik değeri olan bir özniteliği tanımlar.

## <a name="BKMK_CppUnitTestAssert_h"></a>CppUnitTestAssert. h

### <a name="BKMK_General_Asserts"></a>Genel onaylar

#### <a name="BKMK_General_Are_Equal"></a>Eşittir
 İki nesnenin eşit olduğunu doğrulama

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki Double 'ın eşit olduğunu doğrulama

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki float 'ın eşit olduğunu doğrulama

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki Char * dizesinin eşit olduğunu doğrulama

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki w_char * dizesinin eşit olduğunu doğrulama

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Not_Equal"></a>Eşit değildir
 İki Double Double 'ın eşit olmadığından emin olun

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki float 'ın eşit olmadığından emin olun

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki Char * dizesinin eşit olmadığından emin olun

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki w_char * dizesinin eşit olmadığından emin olun

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki başvuruyu işleç = = işlecine göre eşit değil olarak doğrulayın.

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Same"></a>Aynı
 İki başvuruyu aynı nesne örneğine (kimlik) başvurmuş olduğunu doğrulayın.

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Not_Same"></a>Aynı değil
 İki başvuruların aynı nesne örneğine (kimlik) başvurmadığından emin olun.

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_Null"></a>Null
 Bir işaretçinin NULL olduğunu doğrulayın.

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_Not_Null"></a>Null değil
 Bir işaretçinin NULL olmadığından emin olun

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_True"></a>Doğru
 Koşulun doğru olduğunu doğrulama

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_False"></a>Yanlış
 Koşulun yanlış olduğunu doğrulama

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Fail"></a>Neden
 Test çalışması sonucunun başarısız olmasını zorla

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="BKMK_WinRT_Asserts"></a>Windows Çalışma Zamanı onayları

#### <a name="BKMK_WinRT_Are_Equal"></a>Eşittir
 İki Windows Çalışma Zamanı işaretçilerinin eşit olduğunu doğrular.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 İki platform:: String ^ dizelerinin eşit olduğunu doğrular.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Same"></a>Aynı
 İki Windows Çalışma Zamanı aynı nesneye başvuruda bulunduğunu doğrular.

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Not_Equal"></a>Eşit değildir
 İki Windows Çalışma Zamanı işaretçilerinin eşit olmadığını doğrular.

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 İki platform:: String ^ dizelerinin eşit olmadığını doğrular.

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Not_Same"></a>Aynı değil
 İki Windows Çalışma Zamanı başvurusunun aynı nesneye başvurmadığını doğrular.

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Is_Null"></a>Null
 Windows Çalışma Zamanı işaretçisinin bir nullptr olduğunu doğrular.

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Is_Not_Null"></a>Null değil
 Windows Çalışma Zamanı işaretçisinin bir nullptr olmadığını doğrular.

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="BKMK_Exception_Asserts"></a>Özel durum onayları

#### <a name="BKMK_Expect_Exception"></a>Özel durum bekliyor
 Bir işlevin özel durum harekete geçirdiğini doğrulayın:

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Bir işlevin özel durum harekete geçirdiğini doğrulayın:

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="BKMK_CppUnitTestLogger_h"></a>Cppunittestgünlükçü. h

### <a name="BKMK_Logger"></a>Medi
 Günlükçü sınıfı, yazılacak statik yöntemler içerir

```
class Logger
```

### <a name="BKMK_Write_Message"></a>Ileti yaz

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>Örnek
 Bu kod bir örneğidir

```
////////////////////////////////////////////////////////////
/* USAGE EXAMPLE
// The following is an example of VSCppUnit usage.
// It includes examples of attribute metadata, fixtures,
// unit tests with assertions, and custom logging.

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Birim testi kod](../test/unit-test-your-code.md) [biriminiz test Gezgini ile yerel kod test Gezgini](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [mevcut C++ uygulamalara birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
