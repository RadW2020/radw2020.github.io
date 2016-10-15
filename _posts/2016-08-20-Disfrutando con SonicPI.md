---
layout: post
title: Disfrutando con SonicPI
---

Esta aplicación merece un post para ella sola.
Voy a hacer una pasada superficial porque el proyecto ha evolucionado tanto que es bastante amplio.
## [SonicPi](http://sonic-pi.net/)
![](http://www.tecoed.co.uk/uploads/1/4/2/4/14249012/8963862_orig.png)

La idea inicial es crear una aplicación para crear música programando. Esto no es totalmente nuevo, pero lo que si es nuevo es com ha conseguido llevarla a cabo, de una manera tan efectiva y atractiva.

El creador ha enfocado la aplicación a hacer sesiones en directo, y anima a sus seguidores a ello. Él lo llama Live Coding. Es algo que practica como el que toca un instrumento, ensayando todas las semanas y haciendo jam sessions, los que tengais un grupo o seais músicos sabéis de qué va ;)


[Ejemplo Live coding Youtube](https://www.youtube.com/watch?v=KJPdbp1An2s)

**¿Quien se puede resistir a este rosa sobre negro mientras generas música electrónica?**
![](https://i.ytimg.com/vi/iJGb8chJHIE/maxresdefault.jpg)

El proyecto ha evolucionado a través del ámbito académico. Posee documentación muy buena para docentes que deseen introducir SonicPi a sus alumnos. Aprender música y programación a la vez que se desarrolla el arte y la creatividad. Sencillamente exquisito.

[SonicPi Lessons for Teachers](https://www.raspberrypi.org/learning/sonic-pi-lessons/
  )

En la web aparecen unos ejemplos donde podemos ver rápidamente de qué trata y qué tipo de sonidos maneja. (Aunque también trabaja con samples, así que si no te gusta el sonido generado por los sintes de software que trae, podemos cargar nuestros cortes de audio o instrumentos en wav)

[Ejemplos sonido SonicPi](http://sonic-pi.net/#examples)


También ha creado un manual de uso que ya quisieran para sí Yamaha, Korg o Moog. Un auténtico lujo totalmente gratuito.

[Manual SonicPi en PDF](https://www.raspberrypi.org/magpi-issues/Essentials_Sonic_Pi-v1.pdf)


Cuando cojo un rato me pongo y engancha bastante. Si te gusta programar, y la música electrónica/ambient, es una gozada.
Aquí dejo un trozo de un cover que he hecho de la canción Blue Monday de New Order.

Si alguien se anima podemos hacer música juntos con un [repo de github](https://github.com/RadW2020/SonicPI_Songs) de por medio :)

#### Blue Monday Cover ####

```

# base loop
define :base do |num|
  num *= 2
  num.times do
    6.times do
      sample :bd_haus , amp: 2
      sleep 0.5
    end

    8.times do
      sample :bd_haus, cutoff: 120, amp: 2
      sleep 0.125
    end
  end
end

# melody loop
define :melodia do |num|
  num.times do
    notes = (ring :F3, :F2, :F3, :F2, :C3, :C2, :C3, :C2, :D3, :D2, :D3, :D2, :D3, :D2, :D3, :D2, :G3, :G2, :G3, :G2, :C3, :C2,:C3, :C2, :D3, :D2, :D3, :D2, :D3, :D2, :D3, :D2 )
    use_synth :chiplead
    use_synth_defaults amp: 0.7, attack: 0.01, sustain: 0.15, release: 0.125, cutoff: 70
    notes.each do |n|
      play note(n)
      sleep 0.25
    end
  end
end

# kick snare loop
define :tumpa do |num|
  num = num * 8
  num.times do
    sample :drum_heavy_kick
    sleep 0.5
    sample :drum_snare_hard , amp: 2
    sleep 0.5
  end
end

#TODO main melody

# break
define :stahp do |num|
  num.times do
    4.times do
      sample :drum_snare_hard, amp: 2
      sleep 0.25
    end
    sleep 0.25
  end
end


########### SONG #############
## Times are normalized to 8 seconds

in_thread do
  base 8
end

in_thread delay: 16 do
  melodia 6
end

in_thread delay: 32 do
  tumpa 4
end

sleep 64
stahp 2

in_thread delay: 66 do
  tumpa 4
end

```
