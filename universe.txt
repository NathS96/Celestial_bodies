--
-- PostgreSQL database dump
--

-- Dumped from database version 12.16 (Ubuntu 12.16-0ubuntu0.20.04.1)
-- Dumped by pg_dump version 12.16 (Ubuntu 12.16-0ubuntu0.20.04.1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(50) NOT NULL,
    description text,
    age_in_billion_years integer,
    galaxy_type character varying(35),
    has_life boolean,
    magnitude numeric(3,2)
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(50) NOT NULL,
    description text,
    age_in_billion_years integer,
    distance_from_earth_in_km integer,
    planet_id integer NOT NULL,
    is_spherical boolean
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: more_info_on_planets; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.more_info_on_planets (
    more_info_on_planets_id integer NOT NULL,
    number_of_moons integer,
    description text,
    core_material character varying(70),
    gravity_in_meter_per_second_squared numeric(4,2),
    name character varying(50) NOT NULL
);


ALTER TABLE public.more_info_on_planets OWNER TO freecodecamp;

--
-- Name: more_info_on_planets_more_info_on_planets_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.more_info_on_planets_more_info_on_planets_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.more_info_on_planets_more_info_on_planets_id_seq OWNER TO freecodecamp;

--
-- Name: more_info_on_planets_more_info_on_planets_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.more_info_on_planets_more_info_on_planets_id_seq OWNED BY public.more_info_on_planets.more_info_on_planets_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(50) NOT NULL,
    size_in_km integer,
    type character varying(50),
    has_life boolean,
    distance_from_earth_in_million_km integer,
    star_id integer NOT NULL
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(50) NOT NULL,
    type character varying(50),
    age_in_billion_years integer,
    distance_from_sun_in_light_years numeric(6,2),
    is_spherical boolean,
    galaxy_id integer NOT NULL
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: more_info_on_planets more_info_on_planets_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.more_info_on_planets ALTER COLUMN more_info_on_planets_id SET DEFAULT nextval('public.more_info_on_planets_more_info_on_planets_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Andromeda', 'The Andromeda Galaxy is a barred spiral galaxy and is the nearest major galaxy to the Milky Way. It was originally named the Andromeda Nebula and is cataloged as Messier 31, M31, and NGC 224. Andromeda has a diameter of about 46.56 kiloparsecs and is approximately 765 kpc from Earth.', 2, 'Barred Spiral', false, 3.44);
INSERT INTO public.galaxy VALUES (2, 'Pinwheel', 'The Pinwheel Galaxy (also known as Messier 101, M101 or NGC 5457) is a face-on spiral galaxy 21 million light-years (6.4 megaparsecs)[5] away from Earth in the constellation Ursa Major. It was discovered by Pierre Méchain in 1781[a] and was communicated that year to Charles Messier, who verified its position for inclusion in the Messier Catalogue as one of its final entries.', 13, 'Spiral', false, 7.90);
INSERT INTO public.galaxy VALUES (3, 'Sombrero', 'The Sombrero Galaxy (also known as Messier Object 104, M104 or NGC 4594) is a peculiar galaxy of unclear classification in the constellation borders of Virgo and Corvus, being about 9.55 megaparsecs (31.1 million light-years) from the Milky Way galaxy.', NULL, NULL, false, 8.00);
INSERT INTO public.galaxy VALUES (4, 'Triangulum', 'The Triangulum Galaxy is a spiral galaxy 2.73 million light-years from Earth in the constellation Triangulum. It is catalogued as Messier 33 or NGC 598.', NULL, 'Spiral', false, 5.72);
INSERT INTO public.galaxy VALUES (5, 'Milky way', 'The Milky Way is the galaxy that includes the Solar System, with the name describing the galaxys appearance from Earth.', 13, 'Barred Spiral', true, 2.20);
INSERT INTO public.galaxy VALUES (6, 'Large Magellanic Cloud', 'The Large Magellanic Cloud is a satellite galaxy of the Milky Way. At a distance of around 50 kiloparsecs, the LMC is the second- or third-closest galaxy to the Milky Way, after the Sagittarius Dwarf Spheroidal and the possible dwarf irregular galaxy called the Canis Major Overdensity.', 1, 'Irregular', false, 0.90);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'Moon', 'The Moon is Earths only natural satellite. It orbits at an average distance of 384400 km, about 30 times the planets diameter.', 5, 4, 4, true);
INSERT INTO public.moon VALUES (2, 'Phobos', 'Phobos is the innermost and larger of the two natural satellites of Mars, the other being Deimos. The two moons were discovered in 1877 by American astronomer Asaph Hall.', 5, 80, 5, false);
INSERT INTO public.moon VALUES (3, 'Deimos', 'Deimos is the smaller and outermost of the two natural satellites of Mars, the other being Phobos.', 5, 78, 5, false);
INSERT INTO public.moon VALUES (4, 'Ganymede', 'Ganymede, or Jupiter III, is the largest and most massive natural satellite of Jupiter as well as in the Solar System, being a planetary-mass moon.', NULL, 628, 6, true);
INSERT INTO public.moon VALUES (5, 'Europa', 'Europa, or Jupiter II, is the smallest of the four Galilean moons orbiting Jupiter, and the sixth-closest to the planet of all the 95 known moons of Jupiter.', NULL, 628, 6, true);
INSERT INTO public.moon VALUES (6, 'Callisto', 'Callisto, or Jupiter IV, is the second-largest moon of Jupiter, after Ganymede.', 5, 628, 6, true);
INSERT INTO public.moon VALUES (7, 'Carpo', 'Carpo, also Jupiter XLVI, is a small outer natural satellite of Jupiter.', 5, NULL, 6, true);
INSERT INTO public.moon VALUES (8, 'Thebe', 'Thebe, also known as Jupiter XIV, is the fourth of Jupiters moons by distance from the planet.', NULL, NULL, 6, false);
INSERT INTO public.moon VALUES (9, 'Adrastea', 'Adrastea, also known as Jupiter XV, is the second by distance, and the smallest of the four inner moons of Jupiter.', 5, 628, 6, false);
INSERT INTO public.moon VALUES (10, 'Themisto', 'Themisto, also known as Jupiter XVIII, is a small prograde irregular satellite of Jupiter.', NULL, NULL, 6, false);
INSERT INTO public.moon VALUES (11, 'Himalia', 'Himalia, or Jupiter VI, is the largest irregular satellite of Jupiter, with a diameter of at least 140 km.', NULL, NULL, 6, false);
INSERT INTO public.moon VALUES (12, 'Dia', 'Dia, also known as Jupiter LIII, is a prograde irregular satellite of Jupiter.', 5, NULL, 6, NULL);
INSERT INTO public.moon VALUES (13, 'Titan', 'Titan is the largest moon of Saturn, the second-largest in the Solar System and larger than any of the dwarf planets of the Solar System.', NULL, 1272, 7, true);
INSERT INTO public.moon VALUES (14, 'Enceladus', 'Enceladus is the sixth-largest moon of Saturn.', 1, 1272, 7, true);
INSERT INTO public.moon VALUES (15, 'Mimas', 'Mimas, also designated Saturn I, is a natural satellite of Saturn that has the second largest crater on any moon in the Solar System, named Herschel.', NULL, 1272, 7, true);
INSERT INTO public.moon VALUES (16, 'Titania', 'Titania, also designated Uranus III, is the largest of the moons of Uranus and the eighth largest moon in the Solar System at a diameter of 1,578 kilometres, with a surface area comparable to that of Australia.', 5, 2723, 8, true);
INSERT INTO public.moon VALUES (17, 'Ariel', NULL, NULL, 2723, 8, true);
INSERT INTO public.moon VALUES (18, 'Neso', 'Neso, also known as Neptune XIII, is the outermost known natural satellite of Neptune.', NULL, 46000, 9, false);
INSERT INTO public.moon VALUES (19, 'Triton', NULL, 5, 4338, 9, true);
INSERT INTO public.moon VALUES (20, 'Carme', 'Carme, or Jupiter V, is the second-largest moon of Jupiter, after Ganymede.', 5, 628, 6, true);


--
-- Data for Name: more_info_on_planets; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.more_info_on_planets VALUES (1, NULL, 'A speculated planet from the Andromeda galaxy', NULL, NULL, 'PA-99-N2');
INSERT INTO public.more_info_on_planets VALUES (2, 0, 'Mercury is the first planet from the Sun and the smallest in the Solar System.', 'Iron', 3.70, 'Mercury');
INSERT INTO public.more_info_on_planets VALUES (3, 0, NULL, 'Nickel and Sulphur', 8.87, 'Venus');
INSERT INTO public.more_info_on_planets VALUES (4, 1, 'Earth, our home planet, is a world unlike any other.', 'Iron and Nickel', 9.81, 'Earth');
INSERT INTO public.more_info_on_planets VALUES (5, 2, 'Mars is the fourth planet and the furthest terrestrial planet from the Sun.', 'Iron', 3.71, 'Mars');
INSERT INTO public.more_info_on_planets VALUES (6, 95, 'Jupiter is the fifth planet from the Sun and the largest in the Solar System.', 'Iron and Silicate', 24.79, 'Jupiter');
INSERT INTO public.more_info_on_planets VALUES (7, 146, 'Saturn is the sixth planet from the Sun and the second-largest in the Solar System, after Jupiter.', 'Hydrogen and Helium', 10.44, 'Saturn');
INSERT INTO public.more_info_on_planets VALUES (8, 27, 'Uranus is the seventh planet from the Sun. It is a gaseous cyan-coloured ice giant.', 'Methane and Ammonia', 8.87, 'Uranus');
INSERT INTO public.more_info_on_planets VALUES (9, 14, 'Neptune is the eighth and farthest planet from the Sun.', 'Iron,Nickel,Silicates', 11.15, 'Neptune');
INSERT INTO public.more_info_on_planets VALUES (10, 5, 'Pluto is a dwarf planet in the Kuiper belt, a ring of bodies beyond the orbit of Neptune.', NULL, 0.62, 'Pluto');
INSERT INTO public.more_info_on_planets VALUES (11, NULL, 'Imaginary planet', NULL, NULL, 'Planet 11');
INSERT INTO public.more_info_on_planets VALUES (12, NULL, 'Imaginary planet', NULL, NULL, 'Alpha');


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'PA-99-N2', NULL, NULL, false, NULL, 1);
INSERT INTO public.planet VALUES (2, 'Mercury', 4880, 'Terrestrial', false, 197, 8);
INSERT INTO public.planet VALUES (3, 'Venus', 6052, 'Terrestrial', false, 131, 8);
INSERT INTO public.planet VALUES (4, 'Earth', 6371, 'Terrestrial', true, 0, 8);
INSERT INTO public.planet VALUES (5, 'Mars', 3390, 'Terrestrial', false, 401, 8);
INSERT INTO public.planet VALUES (6, 'Jupiter', 69911, 'Gas giant', false, 601, 8);
INSERT INTO public.planet VALUES (7, 'Saturn', 58232, 'Gas giant', false, 1434, 8);
INSERT INTO public.planet VALUES (8, 'Uranus', 25362, 'Ice giant', false, 2786, 8);
INSERT INTO public.planet VALUES (9, 'Neptune', 24622, 'Ice giant', false, 4396, 8);
INSERT INTO public.planet VALUES (10, 'Pluto', 1151, 'Dwarf planet', false, 5283, 8);
INSERT INTO public.planet VALUES (11, 'Planet 11', NULL, NULL, true, NULL, 3);
INSERT INTO public.planet VALUES (12, 'Alpha', NULL, NULL, true, NULL, 2);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 'Delta Andromedae', 'giant', 3, 105.50, true, 1);
INSERT INTO public.star VALUES (2, 'Xi Andromedae', 'Subgiant', NULL, 223.00, true, 1);
INSERT INTO public.star VALUES (3, 'Mizar', 'Spectral Type', 370, 83.00, false, 2);
INSERT INTO public.star VALUES (4, 'Alcor', 'Red dwarf', 1, 82.00, true, 2);
INSERT INTO public.star VALUES (5, 'Alpha Trianguli', NULL, 2, 63.00, true, 4);
INSERT INTO public.star VALUES (6, 'Pistol Star', 'luminous blue hypergiant', 4, 2500.00, true, 5);
INSERT INTO public.star VALUES (7, 'S Doradus', 'Blue supergiant variable', 10, 1890.00, true, 6);
INSERT INTO public.star VALUES (8, 'Sun', 'yellow dwarf', 5, 0.00, true, 5);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 6, true);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 20, true);


--
-- Name: more_info_on_planets_more_info_on_planets_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.more_info_on_planets_more_info_on_planets_id_seq', 12, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 12, true);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 8, true);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: more_info_on_planets more_info_on_planets_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.more_info_on_planets
    ADD CONSTRAINT more_info_on_planets_name_key UNIQUE (name);


--
-- Name: more_info_on_planets more_info_on_planets_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.more_info_on_planets
    ADD CONSTRAINT more_info_on_planets_pkey PRIMARY KEY (more_info_on_planets_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: more_info_on_planets more_info_on_planets_name_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.more_info_on_planets
    ADD CONSTRAINT more_info_on_planets_name_fkey FOREIGN KEY (name) REFERENCES public.planet(name);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

