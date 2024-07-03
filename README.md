# Tailwind works

Примеры работ с использованием Tailwind

## Group

Использование групп для появления элементов при наведении:

    <div
      className="group bg-transparent flex w-full mx-auto justify-between items-center hover:bg-root-card-light dark:hover:bg-root-card-dark transition rounded p-3">
      <div className="flex items-center gap-3">
        <Button color="primal" onClick={handleStartMusic}><FaPlay className="cursor-pointer" /></Button>
        <h1 className="text-ellipsis overflow-hidden max-w-[250px] whitespace-nowrap">{music.name}</h1>
      </div>
      <div className="flex items-center gap-5">
        <h1 className="group-hover:hidden">{music.timeMusic}</h1>
        <Dropdown arrowIcon={false} className="hidden group-hover:block" inline placement="right-start"
          label={<SlOptions className="hidden group-hover:block" size={25} />}>
          <Dropdown.Item className="p-2 hover:bg-root-greyLight transition"
          onClick={handleDeleteMusic}>Удалить</Dropdown.Item>
          <Dropdown.Item className="p-2 hover:bg-root-greyLight transition">Редактировать</Dropdown.Item>
        </Dropdown>
      </div>
    </div>

В этом примере мы используем класс group для создания эффекта наведения курсора мыши, который раскрывает дополнительные элементы, когда пользователь наводит курсор мыши на контейнер. Класс group-hover - это служебный класс, предоставляемый Tailwind, который позволяет нам стилизовать элементы на основе состояния наведения курсора мыши на их родительский элемент.

## Кастомный config

Настраивал конфиг под себя, что бы использовать собственные параметры размеров окна, библиотеку цветов, шрифты и тд.

    /** @type {import('tailwindcss').Config} */
    export default {
        content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}', flowbite.content()],
        darkMode: 'class',
        theme: {
            screens: {
            'sm': { 'max': '750px' },
            'md-list': { 'max': '1000px' }
        },
        extend: {
            colors: {
                root: {
                    violet: {
                        default: '#9605ca',
                        hover: '#7f05ab',
                    },
                    bg: {
                        dark: '#242424',
                        light: '#efefef',
                    },
                    card: {
                        dark: '#1a1a1a',
                        light: '#e3e3e3',
                    },
                },
            },
            gridTemplateColumns: {
                autoFill: 'repeat(auto-fill, minmax(250px, 1fr))',
            },
            fontFamily: {
                Ubuntu: ['Ubuntu', { fontFeatureSettings: 'kern' }],
            },
        },
    },
    plugins: [flowbite.plugin()],
    }

## Кастомный Checkbox и Dropdown

Писал кастомные checkbox и dropdown элементы:

    <Dropdown
      label=""
      renderTrigger={() => (
        <div
          className={`cursor-pointer ${isDisabled ? 'pointer-events-none' : ''} border-root-violet-default dark:bg-root-card-dark flex w-fit items-center justify-between rounded border bg-root-card-light p-2`}
        >
          <div className="flex items-center gap-2">{activeElement}</div>
          <RiArrowDropDownLine size={20} className="justify-end" />
        </div>
      )}
    >
      {passiveElements.map((element, index) => (
        <div key={index}>{element}</div>
      ))}
    </Dropdown>

    <div class="inline-flex items-center">
      <label class="relative flex items-center p-3 rounded-full cursor-pointer" htmlFor="checkbox">
        <input type="checkbox"
          class="before:content[''] peer relative h-5 w-5 cursor-pointer appearance-none rounded-md border border-blue-gray-200 transition-all before:absolute before:top-2/4 before:left-2/4 before:block before:h-12 before:w-12 before:-translate-y-2/4 before:-translate-x-2/4 before:rounded-full before:bg-blue-gray-500 before:opacity-0 before:transition-opacity checked:border-gray-900 checked:bg-gray-900 checked:before:bg-gray-900 hover:before:opacity-10"
          id="checkbox" checked />
        <span
          class="absolute text-white transition-opacity opacity-0 pointer-events-none top-2/4 left-2/4 -translate-y-2/4 -translate-x-2/4 peer-checked:opacity-100">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 20 20" fill="currentColor"
            stroke="currentColor" stroke-width="1">
            <path fill-rule="evenodd"
              d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
              clip-rule="evenodd"></path>
          </svg>
        </span>
      </label>
    </div> 

## Анимации

Совсем немного баловался с анимациями, знаком с ними хорошо, но в tailwind мало использовал

    <div class="my-40 flex">
      <div class="relative mx-auto h-10 w-10 animate-bounce">
        <div class="mx-auto h-16 w-16 animate-pulse rounded-full bg-gray-400"></div>
        <span class="absolute flex h-5 w-5 animate-spin">
          <span class="h-4 w-4 rounded-full bg-gray-400"> </span>
        </span>
      </div>
    </div>

## Сетка Grid для товаров

Самая обычная сетка для расположения товаров

    <div className="container mx-auto my-96">
      <div className="grid md:grid-cols-2 sm:grid-cols-1 lg:grid-cols-4 gap-4">
        {products.map((product, index) => (
          <Product
            key={index}
            _id={product._id}
            img={product.img}
            productName={product.productName}
            price={product.price}
            color={product.color}
          />
        ))}
      </div>
    </div>

### Постарался найти все, чем занимался, если есть конкретные вопросы или может тестовое задание, то готов выполнить