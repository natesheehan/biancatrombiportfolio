<script>
    import Menu from "$lib/components/menu.svelte";
</script>

<Menu />

<style>
.container {
    max-width: 900px;
    margin: 5% auto;
    padding: 1rem;
    color: white;
    font-family: Avenir, sans-serif;
    margin-top: 15%;
}

.album {
    display: flex;
    align-items: center;
    gap: 2rem;
    margin-bottom: 3rem;
}

/* Image styles */
.album img {
    width: 40%;
    max-width: 300px;
    border-radius: 8px;
}

/* Text content */
.album-text {
    flex: 1;
    text-align: justify;
    font-size: 0.9rem;
}

/* Headings */
.album h1 {
    font-size: 1.8rem;
    margin-bottom: 0.5rem;
}

/* Mobile responsive */
@media (max-width: 768px) {
    .album {
        flex-direction: column;
        text-align: center;
    }
    
    .album img {
        width: 80%;
    }

    .album-text {
        font-size: 1rem;
        text-align: left;
    }

    .album h1 {
        font-size: 1.5rem;
        text-align: center;
    }
    .container{
        margin-top:50%;
    }
}
</style>

<div class="container">
    <div class="album">
        <img src="albums/malikai.jpeg" alt="Malikai Album Cover">
        <div class="album-text">
            <h1>MÁLIKAI</h1>
            <p>The album explores the subtle and intricate qualities of the colours produced through the harp and the transformative nature of its tones through
                extended techniques. Inspired by Málikai, ceremonial songs performed during rites of passage in Wakuénai cosmologies, the album creates
                mystical soundscapes that transcend conventional instrumental approaches by exploring diverse physical methods of sound synthesis. </p>
            <p>The harp’s materiality is deconstructed into its individual and perceptual qualities, which are then reconstructed to create new perceptions of
                instrumental sounds. Drawing inspiration from ceremonial instruments used in prayer and rituals, such as gongs, cymbals, and drums, DIY mallets
                are used to produce a range of tones by striking, sliding, and rubbing the harp body.</p>
            <p>Materials and actions are translated into sound—plucking, hitting, sliding, striking, bending—using elements like paper, rubber, foil, and metal to
                interact with the harp strings and body. These physical interactions give rise to a mesmerizing array of metallic and fluidic textures, from gong-like
                resonances to howling echoes and double bass tones. Bow strokes transform the harp into a drone fuzzy violin, while pitch bending and detuning
                evoke esoteric sounds. This exploration of electro-acoustic nuances and vibrational textures resonates with the sounds of the other-than-human
                world, creating an enchanting communion of sound.</p>
        </div>
    </div>

    <div class="album">
        <img src="albums/heliconia.jpeg" alt="Heliconia Album Cover">
        <div class="album-text">
            <h1>HELICONIA</h1>
            <p>Recorded in between England and Brazil, the album is an intimate journey through ambient soundscapes with ethereal textures,
                meditative melodies, and rhythmic patterns. Constructed from unwritten improvisations, strings intertwine with field recordings from
                tropical islands, flutes, shakers, and local drums gathered throughout my travels. Environmental textures create a dialogue between
                nature and melody, narrating sonic tales inspired by the Brazilian rich landscapes. </p>
            <p>In this collection, the harp moves beyond its ornamental role and becomes the driving sound, shaping rhythms, patterns, and movement.
                Each track is named after a tree from Brazil’s rainforests, grounding the music in the natural landscape that inspired it. Every song was
                recorded at different coordinates, turning the album into a personal, experimental journey through both place and memory.</p>
        </div>
    </div>

    <div class="album">
        <img src="albums/live.jpeg" alt="Live//uncut Album Cover">
        <div class="album-text">
            <h1>LIVE//uncut</h1>
            <p>Unedited and uncut, this album consists of long, pure, uninterrupted takes that explore free improvisation as a tool for storytelling.</p>
            <p>These compositions explore change and repetition, spontaneous melodies weaving in silence to create blissful ambiances and delicate
                lullabies from the harp. Tapestry of echoes gradually builds, shaping distinct rhythms and moments of musical clarity. Embracing the
                gifts and flaws of improvisation, I found a raw beauty in the natural performance. .</p>
        </div>
    </div>
</div>
