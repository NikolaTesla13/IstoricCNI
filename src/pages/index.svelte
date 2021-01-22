<script>
    import { metatags } from '@roxi/routify'
    metatags.title = 'Colegiul National Iasi'
    metatags.description = 'Description coming soon...'

    import { 
        Fullpage,
        FullpageSection
    } from 'svelte-fullpage';

    const sections = [
        'Colegiul National Iasi',
        '1828',
        '1834',
        '1860-1864',
        '1890-1894',
        '1903',
        '1916-1918',
        '1922',
        '1926',
        '1944',
        '1948',
        '1998'
    ];

    const text = [
        '193 de ani de excelenta',
        'Istoria liceului începe la 23 ianuarie 1828, când cărturarul Gheorghe Asachi înfiinţează “Gimnaziul Vasilian”, prin completarea şcolii primare de la Mânăstirea Trei Ierarhi cu clase gimnaziale, având ca limbă de predare română. ',
        'Din “Gimnaziul Vasilian” se dezvolta “Academia Mihaileana”, la 20 martie 1834, prima institutie de invatamant superior din tara la acea vreme. ',
        'Funcționează ca liceu sub denumirea "Colegiul National"',
        'Vechea cladire a Lic. National este inlocuita cu un nou edificiu (actualul corp A)',
        'Apare primul numar al revistei elevilor liceului "Spre Luminã”',
        'In anii razboiului pentru întregirea neamului, cladirea şcolii este sediul „Spitalului Crucii Roşii”',
        'se infiinteaza un camin pentru copiii de la tara, cu intretinere complet gratuita a in jur de 30 de elevi selectionati prin concurs de bursa din principalele comune ale Jud. Iasi. Acestia sunt insa obligati sa poarte numai costum national.',
        'Este instituit şi sfinţit noul drapel al Liceului Naţional, menit sa-l înlocuiascã pe cel vechi, din 1828, al Şcolii Vasiliene şi al Academiei Mihãilene',
        'Intre 29 martie 1944 - 15 martie 1945,liceul este evacuat, datoritã operaţiunilor militare de pe frontul din Moldova, la Faget-Lugoj.',
        'In perioada 1948 - 1977 scoala functioneaza sub diferite denumiri (Liceul de Bãieţi Nr.1, Liceul "Mihail Sadoveanu", Liceul de matematicã-fizicã Nr.1 "Mihail Sadoveanu") , intre care s-a impus cea de Liceul Mihail Sadoveanu. Dupa care in 1978 se revine la vechiul nume de Liceul National.',
        'Scoala isi reia numele de Colegiul National.'
    ];

    const images = [
        'images/cni1.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg',
        'images/academie.jpg'
    ];

    let activeSection = 0;

    const goToYear = (name) => {
        activeSection = sections.indexOf(name);
    }
</script>

<main>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-giJF6kkoqNQ00vy+HMDP7azOuL0xtbfIcaT9wjKHr8RbDVddVHyTfAAsrekwKmP1" crossorigin="anonymous">
    <nav class="navbar navbar-expand-lg navbar-light bg-light" style="z-index: 5">
    <div class="container-fluid">
      <a class="navbar-brand" href="#" on:click={() => goToYear("Colegiul National Iasi")}>Istoric</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarText">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            {#each sections as name}
                {#if sections.indexOf({name}.name) !== 0}
                    <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="#" on:click={() => goToYear({name}.name)}>{name}</a>
                    </li>
                {/if}
            {/each}
        </ul>
        <span class="navbar-text">
          Realizat de Asandei Stefan
        </span>
      </div>
    </div>
  </nav>
    <Fullpage bind:activeSection {sections} arrows>
        {#each sections as name}
            <FullpageSection sectionId={sections.indexOf({name}.name).toString()} bind:activeSection center>
                <div class="container">
                    <div class="row">
                        <div class="col-sm">
                            <h1>{{name}.name}</h1>
                            <h3>{text[sections.indexOf({name}.name)]}</h3>
                        </div>
                        <div class="col-sm">
                            <!-- svelte-ignore a11y-img-redundant-alt -->
                            <img src={images[sections.indexOf({name}.name)]} class="img-fluid" alt="image">
                        </div>
                    </div>
                </div>
            </FullpageSection>
        {/each}
    </Fullpage>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-ygbV9kiqUc6oa4msXn9868pTtWMgiQaeYH7/t7LECLbyPA2x65Kgf80OJFdroafW" crossorigin="anonymous"></script>
</main>