# pet-parks

Project Description:
  This project uses spring boot to create tables inside of a database, and ARC commands to update the database using http requests. 
  The tables have the locations of pet parks and what you can do at them, as well as information about visitors.

 Technologies used:

   1. eclipse IDE
   2. ARC
   3. spring.io
   4. draw.io
   5. DBeaver
   6. MySQL Workbench

Favorite Features: 

  The annotations that are used help generate boilerplate code so that you can focus on more complex functionality.

Code Snippet:

  @Entity
@Data
public class PetPark {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long petParkId;

	private String parkName;
	private String directions;
	private String stateOrProvince;
	private String country;

	@Embedded
	private GeoLocation geoLocation;

	@EqualsAndHashCode.Exclude
	@ToString.Exclude
	@ManyToOne(cascade = CascadeType.ALL)
	@JoinColumn(name = "contributor_id", nullable = false)
	private Contributor contributor;

	@EqualsAndHashCode.Exclude
	@ToString.Exclude
	@ManyToMany(cascade = CascadeType.PERSIST)
	@JoinTable(name = "pet_park_amenity",
	joinColumns = @JoinColumn(name = "pet_park_id"),
	inverseJoinColumns = @JoinColumn(name = "amenity_id"))
	private Set<Amenity> amenities = new HashSet<>();

 Here the annotations really shine. They help establish the entity relationships and they also use lombok to create code.

Usage:

  Simply pull the repo into an IDE. You will need the lombok software, as well as a YAML editor and SQL editor.

  
