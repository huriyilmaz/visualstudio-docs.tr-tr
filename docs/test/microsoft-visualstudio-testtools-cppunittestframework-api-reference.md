---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API'si
description: Bu makalede, Microsoft Yerel Birim Testi Çerçevesi'ne göre C++ birim testleri yazmak için kullanabileceğiniz CppUnitTestFramework üyeleri açıklanmıştır.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 8530bcdcdd47a57d97260a1b48f05df1e8661b80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092247"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API başvurusu

Bu konu, ad alanının genel üyelerini `Microsoft::VisualStudio::CppUnitTestFramework` listeler. Microsoft Yerel Birim Testi Çerçevesi'ne göre C++ birim testleri yazmak için bu API'leri kullanın. Konunun sonunda [bir](#example) Kullanım Örneği vardır.

Üst bilgi ve lib dosyaları *\<Visual Studio installation folder> \VC\Auxiliary\VS\UnitTest altında bulunur.*

Üst bilgi ve lib yolları, Yerel Test projesinde otomatik olarak yapılandırılır.

## <a name="in-this-topic"></a><a name="In_this_topic"></a> Bu konu başlığında

[CppUnitTest.h](#cppUnitTest_h)

- [Test sınıfları ve yöntemleri oluşturma](#create_test_classes_and_methods)

- [Başlatma ve temizleme](#Initialize_and_cleanup)

  - [Test yöntemleri](#test_methods)

  - [Test sınıfları](#test_classes)

  - [Test modülleri](#test_modules)

- [Test öznitelikleri oluşturma](#create_test_attributes)

  - [Test yöntemi öznitelikleri](#test_method_attributes)

  - [Test sınıfı öznitelikleri](#test_class_attributes)

  - [Modül özniteliklerini test etmek](#test_module_attributes)

  - [Önceden tanımlanmış öznitelikler](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Genel Onaylamalar](#general_asserts)

    - [Eşittir](#general_are_equal)

    - [Eşit Değildir](#general_are_not_equal)

    - [Aynı](#general_are_same)

    - [Aynı Değil](#general_are_not_same)

    - [Is Null](#general_is_null)

    - [Null Değil](#general_is_not_null)

    - [Is True](#general_is_True)

    - [Yanlış](#general_is_false)

    - [Başarısız](#general_Fail)

  - [Windows Çalışma Zamanı Onaylamaları](#winrt_asserts)

    - [Eşittir](#winrt_are_equal)

    - [Aynı](#winrt_are_same)

    - [Eşit Değildir](#winrt_are_not_equal)

    - [Aynı Değil](#winrt_are_not_same)

    - [Is Null](#winrt_is_null)

    - [Null Değil](#winrt_is_not_null)

  - [Özel Durum Onaylamaları](#exception_asserts)

    - [Özel Durum Bekle](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Günlükçü](#logger)

    - [İleti Yazma](#write_message)

  - [Kullanım Örneği](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> Test sınıfları ve yöntemleri oluşturma

```cpp
TEST_CLASS(className)
```

Test yöntemlerini içeren her sınıf için gereklidir. *className'i* bir test sınıfı olarak tanımlar. `TEST_CLASS` ad alanı kapsamında bildir gerekir.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

*methodName'i* test yöntemi olarak tanımlar. `TEST_METHOD` yönteminin sınıfının kapsamında bildir gerekir.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> Başlatma ve temizleme

#### <a name="test-methods"></a><a name="test_methods"></a> Test yöntemleri

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

*methodName'i,* her test yöntemi çalıştırılamadan önce çalışan bir yöntem olarak tanımlar. `TEST_METHOD_INITIALIZE` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

*methodName'i* her test yöntemi çalıştırildikten sonra çalıştıran bir yöntem olarak tanımlar. `TEST_METHOD_CLEANUP` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

#### <a name="test-classes"></a><a name="test_classes"></a> Test sınıfları

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

*methodName'i* her test sınıfı oluşturulmadan önce çalıştırılan bir yöntem olarak tanımlar. `TEST_CLASS_INITIALIZE` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

*methodName'i* her test sınıfı oluşturulduktan sonra çalıştırılan bir yöntem olarak tanımlar. `TEST_CLASS_CLEANUP` , bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfının kapsamında tanımlanmalıdır.

#### <a name="test-modules"></a><a name="test_modules"></a> Test modülleri

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Bir modül *yüklendiğinde çalışan methodName* yöntemini tanımlar. `TEST_MODULE_INITIALIZE` bir test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirlanmalıdır.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Bir modül kaldırılmış olduğunda çalışan *methodName* yöntemini tanımlar. `TEST_MODULE_CLEANUP` bir test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirlanmalıdır.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> Test öznitelikleri oluşturma

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> Test yöntemi öznitelikleri

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

testMethodName test yöntemine bir veya daha fazla makro `TEST_METHOD_ATTRIBUTE` ile *tanımlanan öznitelikleri ekler.*

Makro, `TEST_METHOD_ATTRIBUTE` attributeName ve *attributeValue* değerine sahip bir *özniteliği tanımlar.*

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> Test sınıfı öznitelikleri

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

testClassName test sınıfına bir veya daha fazla makro `TEST_CLASS_ATTRIBUTE` ile tanımlanan *öznitelikleri ekler.*

Makro, `TEST_CLASS_ATTRIBUTE` attributeName ve *attributeValue* değerine sahip bir *özniteliği tanımlar.*

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> Modül özniteliklerini test etmek

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

testModuleName test modülüne bir veya daha fazla makro `TEST_MODULE_ATTRIBUTE` ile *tanımlanan öznitelikleri ekler.*

Makro, `TEST_MODULE_ATTRIBUTE` attributeName ve *attributeValue* değerine sahip bir *özniteliği tanımlar.*

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> Önceden tanımlanmış öznitelikler

Bu önceden tanımlanmış öznitelik makroları, yaygın durumlar için kolaylık sağlamak amacıyla sağlanır. Bunlar, yukarıda açıklanan makronun `TEST_METHOD_ATTRIBUTE` yerine 2.

```cpp
TEST_OWNER(ownerAlias)
```

`TEST_METHOD_ATTRIBUTE` `Owner` ownerAlias'ın adıyla ve öznitelik *değeriyle bir tanımlar.*

```cpp
TEST_DESCRIPTION(description)
```

açıklamanın `TEST_METHOD_ATTRIBUTE` adıyla ve öznitelik `Description` değeriyle bir *tanımlar.*

```cpp
TEST_PRIORITY(priority)
```

önceliğe `TEST_METHOD_ATTRIBUTE` sahip bir adını ve öznitelik değerini `Priority` *tanımlar.*

```cpp
TEST_WORKITEM(workitem)
```

adı `TEST_METHOD_ATTRIBUTE` ve `WorkItem` workItem özniteliği *değerine sahip bir tanımlar.*

```cpp
TEST_IGNORE()
```

adıyla `TEST_METHOD_ATTRIBUTE` ve öznitelik `Ignore` değeriyle bir `true` tanımlar.

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="general_asserts"></a> Genel Onaylamalar

#### <a name="are-equal"></a><a name="general_are_equal"></a> Eşittir
İki nesnelerin eşit olduğunu doğrulama

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki çiftin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki float'ın eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki karakter* dizenin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki farklı w_char* dizenin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> Eşit Değildir
İki çiftin eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki float'ın eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki karakter* dizenin eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki farklı w_char* dizenin eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

operator== temel alarak iki başvuru arasında eşit olmadığını doğrulayın.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> Aynı
İki başvuruyu aynı nesne örneğine (kimlik) başvurmuş olduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> Aynı değil
İki başvuruların aynı nesne örneğine (kimlik) başvurmadığından emin olun.

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> Null
Bir işaretçinin NULL olduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> Null değil
Bir işaretçinin NULL olmadığından emin olun

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> Doğru
Koşulun doğru olduğunu doğrulama

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> Yanlış
Koşulun yanlış olduğunu doğrulama

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> Neden
Test çalışması sonucunun başarısız olmasını zorla

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a>Windows Çalışma zamanı onayları

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> Eşittir
iki Windows Çalışma Zamanı işaretçilerinin eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

İki platform:: String ^ dizelerinin eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> Aynı
iki Windows Çalışma Zamanı aynı nesneye başvuruda bulunduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> Eşit değildir
iki Windows Çalışma Zamanı işaretçilerinin eşit olmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

İki platform:: String ^ dizelerinin eşit olmadığını doğrular.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> Aynı değil
iki Windows Çalışma Zamanı başvurusunun aynı nesneye başvurmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> Null
Windows Çalışma Zamanı işaretçisinin bir nullptr olduğunu doğrular.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> Null değil
Windows Çalışma Zamanı işaretçisinin bir nullptr olmadığını doğrular.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> Özel durum onayları

#### <a name="expect-exception"></a><a name="expect_exception"></a> Özel durum bekliyor
Bir işlevin özel durum harekete geçirdiğini doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Bir işlevin özel durum harekete geçirdiğini doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> Cppunittestgünlükçü. h

### <a name="logger"></a><a name="logger"></a> Medi
Günlükçü sınıfı, **Çıkış penceresi** yazılacak statik yöntemler içerir.

### <a name="write-message"></a><a name="write_message"></a> Ileti yaz
**Çıkış penceresi** bir dize yazın

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a> Örneğinde
Bu kod, VSCppUnit kullanımının bir örneğidir. Öznitelik meta verileri, armatürler, onaylamaları olan birim testleri ve özel günlüğe kaydetme örneklerini içerir.

```cpp
// USAGE EXAMPLE

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

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
