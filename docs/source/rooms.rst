Rooms Class
============

Room Entity
-----------

.. code-block:: java

  @Id
  @GeneratedValue
  private Long id;

  @Column(nullable=false)
  private Integer floor;

  @Column(nullable=false)
  private String name;

  @OneToOne
  private SensorEntity currentTemperature;

  @Column
  private Double targetTemperature;

  @OneToMany(mappedBy = "room", fetch = FetchType.EAGER)
  private Set<WindowEntity> windows = Set.of();

  @OneToMany(mappedBy = "room", fetch = FetchType.EAGER)
  private Set<HeaterEntity> heaters = Set.of();

  @ManyToOne(optional = false)
  private BuildingEntity building;


Room Controller
-----------

.. code-block:: java

  private final RoomDao roomDao;
  private final WindowDao windowDao;
  private final HeaterDao heaterDao;
  private final BuildingDao buildingDao;
  private final SensorDao sensorDao;
