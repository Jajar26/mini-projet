Mini-projet : 

NERNEL — Reconnaissance et désambiguïsation d'entités nommées 

NERNEL est un outil Python basé sur les modèles Transformers qui permet de : 

- détecter les entités nommées dans un texte (NER)
- les désambiguïser en les associant à leur titre Wikipédia le plus pertinent (NED)
- les remplacer dans le texte pour plus de clarté et de précision

Fonctionnalités : 

- Reconnaissance d'entités nommées multilingue avec le modèle `wikineural-multilingual-ner`
- Désambiguïsation via Wikipédia avec le modèle `facebook/mgenre-wiki`
- Remplacement automatique des entités par leur titre Wikipédia
- Gestions des textes multilingues et des entités ambiguës (ex. Newton)

Exemples : 

    model = NERNEL()

    text_example = """Einstein was a physicist. Tesla cars run on electric batteries. Newton mede la fuerza. El Newton es la medida para cuantificar la fuerza. Hilton investit. Je vais dormir au Hilton cette nuit."""
    
    print(model.text_split(text_example))
    
    long_text_example = """Hugo a écrit plusieurs œuvres qui ont marqué la littérature française, notamment une histoire se déroulant sous les arches de Notre-Dame. En 1831, son roman a provoqué un vif intérêt à Paris. Meanwhile, in London, Dickens was publishing Oliver Twist, a novel that exposed the harsh realities of child labor. Hugo’s influence reached beyond France, inspiring writers across Europe. En Espagne, Cervantes est considéré comme un pionnier du roman moderne. Don Quijote sigue siendo una obra fundamental en la literatura hispánica. À la même époque, Hugo participait à des débats politiques sur la condition des pauvres. He was deeply involved in the social movements of his time, advocating for justice and equality."""
    
    print(model.text_split(long_text_example))

Sorties : 

Albert Einstein was a physicist. Tesla, Inc. cars run on electric batteries. Newton mede la fuerza. El Newton (unidad) es la medida para cuantificar la fuerza. Hilton Worldwide investit. Je vais dormir au Hilton (entreprise) cette nuit. .

Victor Hugo a écrit plusieurs œuvres qui ont marqué la littérature française, notamment une histoire se déroulant sous les Arches de Notre-Dame. En 1831, son roman a provoqué un vif intérêt à Paris. Meanwhile, in East End of London, Charles Dickens was publishing Oliver Twist, a novel that exposed the harsh realities of child labor. Victor Hugo’s influence reached beyond France, inspiring writers across Europe. En Espagne, Miguel de Cervantes est considéré comme un pionnier du roman moderne. Don Quijote de la Mancha sigue siendo una obra fundamental en la literatura hispánica. À la même époque, Victor Hugo participait à des débats politiques sur la condition des pauvres. He was deeply involved in the Social equality movements of his time, advocating for justice and equality. .
